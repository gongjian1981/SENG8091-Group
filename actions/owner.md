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
