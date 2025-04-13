# Non-Functional Requirements

## 1. Performance Requirements

- As a user, I want the app to load the business map within 2 seconds so I can start exploring quickly.
- As a user, I expect business profiles and promotion details to load within 2 seconds after tapping.
- As a user, I expect check-in validation to complete within 1 second so I can earn points promptly.
- As a user, I expect other actions' response within 3 second.
- As a user, I hope the system stays stable when 1,000 or fewer users are using the app at the same time.

## 2. Security Requirements

- As a user, I can log in securely using my email and password, which are encrypted.
- As a user, I hope my personal data will be transmitted over HTTPS and stored securely using modern encryption.
- As a business user, I can only access and manage my own business data.
- As a system admin, I can access the system through a secure admin-only login portal.
- As a system admin, I can get notified if there is any suspicious behaviors (e.g., excessive check-ins) detected.

## 3. Usability Requirements

- As a first-time user, I can understand how to check in and redeem a reward within 5 minutes without help.
- As a user, I can use the app easily because of its clean, mobile-first design and intuitive navigation.
- As a user with disabilities, I can navigate the app with screen readers and high-contrast settings.
- As a business user, I can understand how to register and public a promotion within 5 minutes without help.

## 4. Reliability & Availability

- As a user, I can expect 99.5% uptime from the platform, excluding planned maintenance.
- As a system admin, I can back up key data (e.g., users, points, businesses) every 12 hours.
- As a system admin, I can restore system functionality within 1 hour if an outage occurs.
- As a system admin, I can ensure that recent changes will not be lost, with a recovery point objective of under 6 hours.

## 5. Scalability Requirements

- As a system admin, I can scale horizontally using containerization tools like Docker.
- As a system admin, I can handle more users by deploying on cloud services like AWS or GCP.
- As a system admin, I can use indexed databases and data partitioning to handle large volumes of check-ins and reviews.
