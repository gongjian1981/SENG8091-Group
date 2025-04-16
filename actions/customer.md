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
