# System Admin Actions Specification

We create actions for implementing system admin functionalities based on [its requirement](../requirements/admin.md).

---

### Requirement 1.1

System admin can log in using a valid admin email and password.

#### Action 1:

Prerequisites: None.

Backend:

> Implement an API that takes `email` and `password` as input. Validate against admin accounts and return an authentication token on success.

Frontend:

> Create an `Admin Login` page with input fields for email and password. On submit, call the API and navigate to the admin dashboard if successful.

### Requirement 1.2

System admin can access all admin tools and dashboards after logging in.

#### Action 2:

Prerequisites: Action 1.

Frontend:

> After successful login, display the admin dashboard with navigation to management sections: Categories, Businesses, Users, Reports, and Settings.

### Requirement 1.3

System admin can securely log out from the admin system.

#### Action 3:

Prerequisites: Action 2.

Frontend:

> Add a `Logout` button in the admin navigation bar. When clicked, clear the stored admin token and redirect to the admin login page.

---

### Requirement 2.1

System admin can view the list of all business categories.

#### Action 4:

Prerequisites: Action 2.

Backend:

> Implement an API that returns all business categories with their `id`, `name`, and `description`.

Frontend:

> Add a `Categories` section in the admin panel that fetches the category list from the API and displays it in a table.

### Requirement 2.2

System admin can create a new business category.

#### Action 5:

Prerequisites: Action 4.

Backend:

> Implement an API that takes `categoryName` and `description` as input and saves a new category to the database.

Frontend:

> Add an `Add Category` button in the `Categories` section. When clicked, show a form for category name and description. On submit, call the API and refresh the list.

### Requirement 2.3

System admin can edit the name or description of an existing category.

#### Action 6:

Prerequisites: Action 4.

Backend:

> Implement an API to update the `name` and `description` of a category using `categoryId`.

Frontend:

> Add an `Edit` button for each category in the list. When clicked, open an edit form with current values. On submit, call the update API and refresh the list.

### Requirement 2.4

System admin can delete a category that is no longer needed.

#### Action 7:

Prerequisites: Action 4.

Backend:

> Implement an API that deletes a category if there are no active businesses using it. Return an error if validation fails.

Frontend:

> Add a `Delete` button for each category. On click, confirm deletion and call the API. Show a success or failure message based on API response.

---

### Requirement 3.1

System admin can view a list of pending business registration requests.

#### Action 8:

Prerequisites: Action 2.

Backend:

> Implement an API that returns all business registrations with status `pending`, along with their submitted information.

Frontend:

> Create a `Pending Businesses` section in the admin dashboard. Fetch the list from the API and display it in a table.

### Requirement 3.2

System admin can approve a business.

#### Action 9:

Prerequisites: Action 8.

Backend:

> Implement an API that updates a business status from `pending` to `approved` and makes it visible on the platform.

Frontend:

> Add an `Approve` button next to each pending business. On click, call the API and update the UI list.

### Requirement 3.3

System admin can reject a business with an optional reason.

#### Action 10:

Prerequisites: Action 8.

Backend:

> Implement an API that sets a business status to `rejected` and saves an optional rejection reason.

Frontend:

> Add a `Reject` button for pending businesses. When clicked, open a text field for rejection reason. On submit, call the API and refresh the list.

### Requirement 3.4

System admin can search and filter business registration requests.

#### Action 11:

Prerequisites: Action 8.

Backend:

> Extend the pending business API to support query parameters: `name`, `categoryId`, `submissionDate`.

Frontend:

> Add search and filter fields to the `Pending Businesses` page. When used, send filter parameters to the API and display the results.

---

### Requirement 4.1

System admin can view all reported reviews or content.

#### Action 12:

Prerequisites: Action 2.

Backend:

> Implement an API that returns a list of reported content including `reportId`, `reviewId`, `reason`, `reporterId`, and timestamp.

Frontend:

> Add a `Reports` section in the admin panel. Fetch and display reported reviews in a table.

### Requirement 4.2

System admin can see the report reason, reporter, and timestamp.

#### Action 13:

Prerequisites: Action 12.

Frontend:

> In the `Reports` section, show columns for report reason, reporter, and report time using the data from the API.

### Requirement 4.3

System admin can mark a report as valid or dismiss it.

#### Action 14:

Prerequisites: Action 13.

Backend:

> Implement an API that takes `reportId` and marks the report as `valid` or `dismissed`.

Frontend:

> Add `Mark as Valid` and `Dismiss` buttons for each report entry. On click, call the API and update the report status in the UI.

### Requirement 4.4

System admin can delete the reported review or content.

#### Action 15:

Prerequisites: Action 14.

Backend:

> Implement an API that deletes the targeted review or content by `reviewId`.

Frontend:

> Add a `Delete Content` button for each reported item. On click, call the API and remove the item from the UI list.

### Requirement 4.5

System admin can send a warning or notice to the user who posted inappropriate content.

#### Action 16:

Prerequisites: Action 14.

Backend:

> Implement an API that sends a notification or warning to the `userId` of the reported content.

Frontend:

> Add a `Send Warning` button for each report. On click, open a text field for the warning message. On submit, call the API and confirm success.

---

### Requirement 5.1

System admin can search for and view user or business accounts.

#### Action 17:

Prerequisites: Action 2.

Backend:

> Implement APIs to search for users and businesses by `name`, `email`, or `businessId`.

Frontend:

> Add a search bar in the `User Management` and `Business Management` sections. When searching, call the API and display matching results.

### Requirement 5.2

System admin can suspend or delete a user account.

#### Action 18:

Prerequisites: Action 17.

Backend:

> Implement an API to change user status to `suspended` or `deleted` based on `userId`.

Frontend:

> Add `Suspend` and `Delete` buttons on the user account page. On click, call the API and refresh the status in the UI.

### Requirement 5.3

System admin can suspend or unpublish a business listing.

#### Action 19:

Prerequisites: Action 17.

Backend:

> Implement an API to set business status to `suspended` or `unpublished` using `businessId`.

Frontend:

> Add `Suspend` and `Unpublish` buttons for each business listing. Call the API when clicked and update the status label in the UI.

### Requirement 5.4

System admin can view reasons for previous suspensions or deletions.

#### Action 20:

Prerequisites: Action 17.

Backend:

> Implement an API that returns the `actionHistory` log for a user or business, including timestamps and reasons for each status change.

Frontend:

> Add a `View History` button for users and businesses. On click, display the list of past actions in a modal.

---
