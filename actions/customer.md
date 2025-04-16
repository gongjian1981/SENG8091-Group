# Customer Actions Specification

We create actions for implementing customer functionalities based on [its requirement](../requirements/customer.md).

### Requirement 1.1

Customer can see an interactive map with pins for each local business.

#### Action 1:

Prerequisites: None.

Backend:

> Implement an API that takes `location` (e.g., latitude and longitude) and `range` (e.g., in kilometers or meters) as input parameters, and returns a list of nearby businesses located within the specified distance from the provided location.

Frontend:

> Develop an interactive map component with touch support, allowing users to zoom in and out using pinch gestures. On every map refresh (e.g., when the user pans or zooms), the frontend sends the current center location and visible range to the backend, and display the result list on the map as pin markers.

### Requirement 1.2

Customer can filter the results by category.

#### Action 2:

Prerequisites: None.

Backend:

> Implement an API that returns all the categories as a list with `id` and `name`.

Frontend:

> Add a select component in the upper right of the map, which can display all the category names which retrieved from the API

#### Action 3:

Prerequisites: Action 2.

Backend:

> Implement an API that takes `location` (e.g., latitude and longitude) and `range` (e.g., in kilometers or meters) and `categoryId` as input parameters, and returns a list of nearby businesses located within the specified distance from the provided location in the specified category.

Frontend:

> When user select one category, add the categoryId as a parameter and call the new API

### Requirement 1.3

Customer can search by keyword and business name, and can sort results by distance, popularity, or rating.

#### Action 4:

Prerequisites: None.

Backend:

> Implement an API that takes `location` (e.g., latitude and longitude) and `range` (e.g., in kilometers or meters) and `keyword` as input parameters, and returns a list of nearby businesses located within the specified distance from the provided location filtered by the keyword.

Frontend:

> Add an input text field in the upper middle of the map, if the user clicks the field, add a button under it named `search`. When user input something, and click search button, call the API and display businesses based on the results.

### Requirement 1.4

Customer can see a business overview on the map when I tap a pin.

#### Action 5:

Prerequisites: None.

Backend:

> Implement an API that takes `businessId` as input parameters, and returns a basic information of the business, including its id, name, category, overview, logo, rating.

Frontend:

> When user click a business pin mark, get the business information from the API and display it.

### Requirement 1.5

Customer can open the business profile page by tapping its name in the overview.

#### Action 6:

Prerequisites: None.

Backend:

> Implement an API that takes `businessId` as input parameters, and returns a detailed information of the business, including its id, name, category, overview, logo, rating, review list, check-in number, .

Frontend:

> Create a business profile page which displays the business's name in the top with its logo, its overview, display its images in the middle, and the rating and all the reviews in the button.

#### Action 7:

Prerequisites: Action 6.

Frontend:

> When user click the business name on a pop-out business pin mark, navigate user to the business profile page.

---

### Requirement 2.1

Customer can check-in only when GPS confirms I am within certain meters (e.g., 50 meters) of the business.

#### Action 8:

Prerequisites: None.

Backend:

> Implement an API that takes `businessId` and `location` as input parameters, if the location is with specified range of the business, and the user hasn't checked in within the last 24 hours, record the check-in action and return true, otherwise return false with reason.

Frontend:

> Add a `check-in` button in the business profile page, and when user click the button call the API.

### Requirement 2.2

Customer can see the result of his check-in.

#### Action 9:

Prerequisites: Action 8.

Frontend:

> When API return true, show a success message, and disable the `check-in` button, and when API return false, show a failure message explaining why.

### Requirement 2.3

Customers cannot check in at the same business again within a 24-hour window.

---

### Requirement 3.1

A login page will be displayed if customer is not logged in when he/her tries to rate or review.

#### Action 10:

Prerequisites: None.

Frontend:

> Add a `rating` button in the business profile page.

#### Action 11:

Prerequisites: Action 10.

Frontend:

> Detect if user is in logged in status when user click `rating` button, if not, navigate to the login page.

### Requirement 3.2

Customer can rate a business through a 1–5 star rating system.

#### Action 12:

Prerequisites: Action 11.

Backend:

> Implement an API that takes `businessId` and `userId` and `rating` as input parameters, save to the database, and return the new average rating of the business.

Frontend:

> After user click the `rating` button. display a modal with 5 outlined stars in a line, user can click certain star and the star and all previous stars will automatically be filled in.
>
> Add a submit button under the stars, when user click the button, call the API, and refresh the rating value with the API's result.

### Requirement 3.3

When customer rates a business, there is an optional text input field where customer can write a review.

#### Action 13:

Prerequisites: Action 12.

Backend:

> Implement an API that takes `businessId` and `userId` and `rating` and `review` as input parameters, save to the database, and return the new average rating of the business and the new list of its reviews.

Frontend:

> Add an input text field under the stars, upon the submit button, when user click the button with the review field left empty, call the API in Action 12; otherwise, call the new API and refresh the rating value and review list with the API's result.

### Requirement 3.4

If customer hasn’t written a review yet, he/her can add one later by clicking my rating.

#### Action 14:

Prerequisites: Action 11.

Backend:

> Implement an API that takes `businessId` and `userId` and `review` as input parameters, update the database, and return the new list of its reviews.

Frontend:

> Add an input text field under the stars, upon the submit button, when user click the button with the text-field left empty, call the API in Action 12; otherwise, call the new API and refresh the rating value and review list with the API's result.

---

### Requirement 3.5

Customer can see all the ratings and reviews and average rating on business profile page.

#### Action 15:

Prerequisites: None.

Backend:

> Implement an API that takes `businessId` as input parameters, return the list of its rating with reviews.

Frontend:

> Create a new window, which call the API and show the list of ratings and reviews for the business.

#### Action 16:

Prerequisites: Action 6, Action 15.

Frontend:

> Add `see all` button under the review list in the business profile page, when user click the button, navigate to the rating and review list page.

---

### Requirement 4.1

Customer can earn points through certain actions (e.g., check-in, rating, review).

#### Action 17:

Prerequisites: None.

Backend:

> Update APIs for check-in (Action 8), rating (Action 12), and review (Action 13) to include logic that assigns a fixed number of points per action type (e.g., 1 point for check-in, 3 for rating, 10 for review). Save points in user reward history and update total points.

Frontend:

> After successful check-in, rating, or review, display a toast message showing points earned. Refresh the total points if the profile tab is open.

### Requirement 4.2

Customer can see how many points they’ve earned immediately after each action.

#### Action 18:

Prerequisites: Action 17.

Backend:

> Modify the response of check-in, rating, and review APIs to include the number of points just earned and total updated points.

Frontend:

> Display a short success message (e.g., "You earned 3 points!") right after the action completes, along with updated total points in the profile tab if visible.

---

### Requirement 5.1

Customer can see a list of redeemable offers with point requirements, and search by keywords.

#### Action 19:

Prerequisites: None.

Backend:

> Implement an API that returns a list of redeemable deals with fields: `dealId`, `title`, `description`, `pointsRequired`, `validUntil`, `businessId`. Support optional keyword query.

Frontend:

> Create a `Deals` tab accessible from the main menu. Display deals in a scrollable list with search input on top. Call the API and display deals with required points and brief info.

### Requirement 5.2

Customer can see redeemable offers of a business on its profile page.

#### Action 20:

Prerequisites: Action 6.

Backend:

> Implement an API that takes `businessId` and returns its available deals.

Frontend:

> In the business profile page, create a `Promotions` section listing all redeemable offers. Display each deal's title, description, and required points.

### Requirement 5.3

A login page will be displayed if customer is not logged in when trying to redeem a reward.

#### Action 21:

Prerequisites: Action 19.

Frontend:

> When user clicks the `Redeem` button on a deal and is not logged in, navigate to the login page before allowing redemption.

### Requirement 5.4

Customer cannot redeem a reward if they don’t have enough points.

#### Action 22:

Prerequisites: Action 21.

Backend:

> In the redeem API, check if user’s total points are sufficient for the selected deal. If not, return an error message.

Frontend:

> When API returns failure due to insufficient points, display an alert message like “Not enough points to redeem this offer.”

### Requirement 5.5

Customer receives a unique code or QR code after redemption.

#### Action 23:

Prerequisites: Action 22.

Backend:

> When a deal is redeemed, generate a unique redemption code or QR and save it in redemption history. Return it in the API response.

Frontend:

> After successful redemption, show the code or QR in a confirmation screen. Allow user to save or screenshot it.

### Requirement 5.6

Customer can see redemption history on the profile page.

#### Action 24:

Prerequisites: Action 23.

Backend:

> Implement an API that returns a list of redeemed deals by user, with fields: `dealTitle`, `redeemedOn`, `code`, and `businessName`.

Frontend:

> Add a `My redemptions` button in the profile tab. When clicked, fetch and display the redemption history in a list format.

---

### Requirement 6.1

Customer can register with their email and set a password.

#### Action 25:

Prerequisites: None.

Backend:

> Implement a registration API that takes `email`, `password`, `name`, and optional `profileImage`, validates input, creates user account, and returns auth token.

Frontend:

> Add a `Register` page with input fields for email, name, password, and profile picture upload. On submit, call the API and navigate to the main app view on success.

### Requirement 6.2

Customer can log in with their email and password.

#### Action 26:

Prerequisites: None.

Backend:

> Implement a login API that takes `email` and `password`, validates credentials, and returns an auth token if successful.

Frontend:

> Add a `Login` page with email and password fields. On success, save the auth token and navigate to the main view.

### Requirement 6.3

Customer can log out from the profile page.

#### Action 27:

Prerequisites: Action 26.

Frontend:

> Add a `Logout` button in the profile tab. When clicked, clear local auth token, reset user state, and navigate back to the login screen.

---
