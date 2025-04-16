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
