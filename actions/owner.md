# Business User Actions Specification

We create actions for implementing business user functionalities based on [its requirement](../requirements/owner.md).

---

### Requirement 1.1

Business user can register a business account with email and password.

#### Action 1:

Prerequisites: None.

Backend:

> Implement an API that takes `email`, `password`, and `businessOwnerName` as input parameters, validates the data, stores the information, and returns a success message or error.

Frontend:

> Create a `Register` page with input fields for email, password, and business owner name. When user clicks the submit button, call the API and navigate to login page on success.

### Requirement 1.2

Business user can log in and log out of their business account.

#### Action 2:

Prerequisites: None.

Backend:

> Implement an API that takes `email` and `password` as input, validates credentials, and returns an authentication token if successful.

Frontend:

> Create a `Login` page with input fields for email and password. On submit, call the API. If successful, save the token and navigate to the dashboard.

#### Action 3:

Prerequisites: Action 2.

Frontend:

> Add a `Logout` button on the business user dashboard. When clicked, clear the token from storage and navigate to the login page.

### Requirement 1.3

Business user can fill out business information after login.

#### Action 4:

Prerequisites: Action 2.

Backend:

> Implement an API that takes `businessId`, `businessName`, `description`, `address`, `businessHours`, `contactInfo`, `logoImage`, and `coverImage` as input parameters, and stores the information in the database.

Frontend:

> Create a `Business Profile Setup` form page for newly registered business users to input the above details. When submitted, call the API and display success or error message.

### Requirement 1.4

Business user can select a category for their business from a predefined list.

#### Action 5:

Prerequisites: None.

Backend:

> Implement an API that returns a predefined list of business categories with `categoryId` and `categoryName`.

Frontend:

> Add a category dropdown to the `Business Profile Setup` form. Fetch the categories from the API and display the list to the user for selection.

### Requirement 1.5

Business user can edit business information later on the business profile page.

#### Action 6:

Prerequisites: Action 4.

Backend:

> Implement an API that allows updating `businessName`, `description`, `address`, `businessHours`, `contactInfo`, `logoImage`, `coverImage`, and `categoryId` for the selected `businessId`.

Frontend:

> Add an `Edit` button to the business profile page. When clicked, load the current data into an editable form. On submit, call the API to save changes and refresh the profile page.

---

### Requirement 2.1

Business user can create a promotion.

#### Action 7:

Prerequisites: Action 4.

Backend:

> Implement an API that takes `businessId`, `title`, `description`, `image`, `pointsRequired`, `startDate`, and `endDate` as input, and saves the promotion to the database.

Frontend:

> Add a `Create Promotion` button on the promotions page. When clicked, open a form for entering the promotion details. On submit, call the API and display a success or error message.

### Requirement 2.2

Business user can edit or delete an existing promotion.

#### Action 8:

Prerequisites: Action 7.

Backend:

> Implement an API to update or delete a promotion using `promotionId` and `businessId`. For updates, allow changes to all fields except `promotionId`.

Frontend:

> Display a list of promotions with `Edit` and `Delete` buttons. When `Edit` is clicked, show a pre-filled form. When `Delete` is clicked, show a confirmation dialog before calling the delete API.

### Requirement 2.3

Business user can view how many times each promotion has been redeemed.

#### Action 9:

Prerequisites: Action 7.

Backend:

> Implement an API that returns a list of promotions for the business, including each `promotionId`, `title`, and `redeemedCount`.

Frontend:

> On the promotions page, display a `Redeemed` counter next to each promotion using the data fetched from the API.

### Requirement 2.4

Business user can pause or resume a promotion.

#### Action 10:

Prerequisites: Action 7.

Backend:

> Implement an API that allows updating a promotion's status field (`active` or `paused`) using `promotionId`.

Frontend:

> Add `Pause` and `Resume` toggle buttons next

---

### Requirement 3.1

Business user can view all ratings and reviews left on their business profile.

#### Action 11:

Prerequisites: Action 4.

Backend:

> Implement an API that takes `businessId` and returns all associated reviews along with rating, reviewer name, review content, and date.

Frontend:

> Add a `Reviews` tab on the business profile page to display reviews fetched from the API in a list format.
