# User Management API Testing (Postman)
 Project Overview
API testing project for a user management module using Postman, covering CRUD operations, authentication, and negative test scenarios. Automated with Newman.

🔧 Tools Used
- Postman
- Newman (CLI automation)
- DummyJSON API (public test API)
- Node.js / npm

 ✅ Test Scenarios Covered

| # | Request | Method | Scenario | Expected Result |
|---|---------|--------|----------|------------------|
| 1 | Get All Users | GET | Fetch list of all users | 200 OK, response contains users array |
| 2 | Get Single User | GET | Fetch user by valid ID | 200 OK, correct user ID returned |
| 3 | Create User | POST | Create a new user | 201 Created, new user has an id |
| 4 | Update User | PUT | Update existing user's firstName | 200 OK, firstName reflects update |
| 5 | Delete User | DELETE | Delete existing user | 200 OK, isDeleted is true |
| 6 | Login | POST | Login with valid credentials | 200 OK, accessToken returned |
| 7 | Get Logged In User | GET | Access protected endpoint using token | 200 OK, correct username returned |
| 8 | Login (Negative) | POST | Login with wrong password | 400 Bad Request, "Invalid credentials" |
| 9 | Get User (Negative) | GET | Fetch user with invalid ID | 404 Not Found, "not found" message |

Total: 9 requests, 25 automated assertions, 0 failures**

 Authentication & Request Chaining
- Captured `accessToken` from Login response using a post-response script
- Stored token in an environment variable (`auth_token`)
- Reused token in Authorization header (Bearer Token) to access a protected endpoint, simulating a real logged-in session
- Encountered and resolved a token-expiry issue during testing, confirming proper token lifecycle handling

How to Run This Project

Option 1: Run in Postman
1. Import `User Management API Testing.postman_collection.json` and `Environment_new.postman_environment.json` into Postman
2. Select the imported environment
3. Run requests individually or use "Run Collection"

Option 2: Run via Newman (CLI Automation)
```bash
npm install -g newman
npm install -g newman-reporter-html
newman run "User Management API Testing.postman_collection.json" -e "Environment_new.postman_environment.json" -r cli,html --reporter-html-export report.html
```

 📊 Test Report
See `report.html` for the full automated test execution report (download and open in browser).


- Writing automated assertions with `pm.test()`
- API test automation using Newman CLI
- Troubleshooting real issues (token expiry) during testing
