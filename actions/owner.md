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
