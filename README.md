# User-Management-API-testing-Postman
API testing project for a user management module using Postman, covering CRUD operations, authentication, and negative test scenarios. Automated with Newman.

# User Management API Testing (Postman)

## 📌 Project Overview
This project demonstrates API testing of a user management module, covering CRUD operations, authentication (login/token), and both positive and negative test scenarios. Testing was performed using Postman, with automated execution via Newman CLI.

## 🔧 Tools Used
- Postman
  

| No. | Test Scenario                   | Method | Expected Result         |
| --- | ------------------------------- | ------ | ----------------------- |
| 1   | Get all users                   | GET    | 200 OK                  |
| 2   | Get user by valid ID            | GET    | 200 OK                  |
| 3   | Get user by invalid ID          | GET    | 404 Not Found           |
| 4   | Create a new user               | POST   | 201 Created             |
| 5   | Update a user                   | PUT    | 200 OK                  |
| 6   | Delete a user                   | DELETE | 200 OK                  |
| 7   | Login with valid credentials    | POST   | 200 OK + Token          |
| 8   | Login with invalid credentials  | POST   | 400/401 Error           |
| 9   | Access protected API with token | GET    | 200 OK                  |
| 10  | Validate response fields        | -      | Required fields present |
| 11  | Check response time             | -      | Less than 1000 ms       |


->Request Chaining
- Captured `user_id` from Create User response and reused it in Get/Update/Delete requests
- Captured `token` from Login response and reused it in protected endpoint headers

->How to Run This Project
1. Clone/download this repository
2. Import `collection.json` and `environment.json` into Postman
3. Select the imported environment
4. Run manually in Postman, OR run via Newman:
