# Mock API Testing – Postman & Newman

This project demonstrates **API testing** using **Postman** with automated validations and execution via **Newman**.

The APIs are provided by **MockAPI**:
🔗 https://mockapi.io/


## 🛠 Tools & Technologies
- Postman
- Newman
- Node.js
- MockAPI
==================================>
Employee API Test Documentation

1- GET ALL EMPLOYEES

Endpoint: /employee

Base URL: https://697f9730d1548030ab667629.mockapi.io/

Method: GET

Response Status: 200 OK

Test Cases Scenarios:

a - Check Status Code is 200
Ensure the API request was successful and returned a 200 OK status.

b - Check Response Time
Ensure the API responds within an acceptable time frame (Less than 800ms).

c - Verify Response Structure (JSON Array)
Confirm that the response body is a valid JSON array, not an object or HTML.

d - Check Data Array is Not Empty
Confirm that the database returns at least one employee record.

e - Validate Data Types for Each Field
Ensure each object in the array contains the correct data types:

id: String

name: String (Length > 0)

phone: String (Length > 0)

salary: Number (Must be >= 0)

married: Boolean

f - Validate Phone Number Format
Check if the phone number matches the allowed pattern (digits, spaces, +, -, ()).

g - Check Unique IDs
Ensure there are no duplicate IDs in the response to guarantee data integrity.

h - Validate Salary Logical Range
Ensure the salary values are within a realistic range (between 0 and 1,000,000).

i - Verify Specific Data Existence
Confirm that a specific critical record (e.g., Employee with ID "1") exists in the database.

j - Schema Validation
Validate the entire JSON response against a strict schema definition to ensure all required fields (id, name, phone, salary, married) are present.

k - Check for Server Errors
Ensure no 4xx (Client Error) or 5xx (Server Error) status codes are returned.
========================================================================================================================================================
2- GET SINGLE EMPLOYEE

Endpoint: /employee/2

Base URL: https://697f9730d1548030ab667629.mockapi.io/

Method: GET

Response Status: 200 OK

Test Cases Scenarios:

a - Check Status Code is 200
Ensure that the request to fetch a single employee returns a successful status code.

b - Check Valid JSON Format
Ensure the response body is a valid JSON object.

c - Verify Required Properties
Confirm that the returned object contains all necessary keys: id, name, phone, salary, and married.

d - Validate Property Types
Ensure that the data types for the returned fields are correct (e.g., id and name are strings, salary is a number).

e - Validate Specific ID
Verify that the API returned the correct employee record requested (ID should equal "2").

f - Validate Salary Range
Ensure the salary for the employee is within the logical limits (0 - 1,000,000).

g - Set Environment Variable
Capture the id from the response and store it as an environment variable (employeeId) to be used in subsequent tests (like Update or Delete).
========================================================================================================================================================
3- CREATE NEW EMPLOYEE

Endpoint: /employee

Base URL: https://697f9730d1548030ab667629.mockapi.io/

Method: POST

Response Status: 201 Created

Test Cases Scenarios:

a - Check Status Code is 201
Ensure the request was successful and the new employee resource was created.

b - Check Valid JSON Format
Ensure the response body is a valid JSON object.

c - Verify Response Properties
Confirm that the response contains the newly created employee data, including: id, name, phone, salary, and married.

d - Validate Data Types
Ensure that the returned fields have the correct data types (e.g., id is string, married is boolean).

e - Check Response Time
Ensure the API responds within 800ms.

f - Set Environment Variable
Capture the newly created id from the response and update the employeeId environment variable for future tests.
========================================================================================================================================================
4- UPDATE EMPLOYEE

Endpoint: /employee/{{employeeId}}

Base URL: https://697f9730d1548030ab667629.mockapi.io/

Method: PUT

Response Status: 200 OK

Test Cases Scenarios:

a - Check Status Code is 200
Ensure the update request was successful and returned a 200 OK status.

b - Check Valid JSON Format
Ensure the response body is a valid JSON object.

c - Verify Header Content-Type
Ensure the server responds with the correct Content-Type: application/json header.

d - Verify Required Properties
Confirm that the updated employee object still contains all necessary keys (id, name, phone, salary, married).

e - Validate Data Types
Ensure that the returned fields maintain their correct data types after the update.

f - Data Consistency (Request matches Response)
Crucial Step: Parse the request body and verify that the values returned by the API match the values sent in the update request. This confirms the update actually happened on the server.

g - Check Response Time
Ensure the API responds within 800ms.

h - Refresh Environment Variable
Update the employeeId environment variable with the returned ID (best practice to ensure continuity).
========================================================================================================================================================
5-EDIT Employee
Endpoint: /employee/{{employeeId}}

Base URL: https://697f9730d1548030ab667629.mockapi.io/

Method: PATCH

Response Status: 200 OK

Test Cases Scenarios:

a - Check Status Code is 200
Ensure the partial update request was successful and returned a 200 OK status.

b - Check Valid JSON Format
Ensure the response body is a valid JSON object.

c - Verify Header Content-Type
Ensure the server responds with the correct Content-Type: application/json header.

d - Schema Validation
Validate the response against a strict JSON schema, ensuring the returned object is complete and valid even after a partial update.

e - Verify Required Properties & Types
Confirm that the returned employee object contains all necessary keys (id, name, phone, salary, married) with correct data types.

f - Data Consistency (Request matches Response)
Crucial Step: Verify that the specific fields sent in the PATCH request body are correctly updated in the response, while other fields remain unaffected (MockAPI usually returns the full object).

g - Check Response Time
Ensure the API responds within 800ms.

h - Refresh Environment Variable
Update the employeeId environment variable with the returned ID.
========================================================================================================================================================
6- DELETE EMPLOYEE

Endpoint: /employee/{{employeeId}}

Base URL: https://697f9730d1548030ab667629.mockapi.io/

Method: DELETE

Response Status: 200 OK

Test Cases Scenarios:

a - Check Status Code
Ensure the delete request was successful. (Note: The provided script checks for 201, but typical REST behavior for DELETE is 200 or 204. MockAPI usually returns 200).

b - Verify Header Content-Type
Ensure the server responds with the correct Content-Type: application/json header.

c - Check Valid JSON Format
Ensure the response body is a valid JSON object.

d - Schema Validation
Validate that the deleted object returned matches the employee schema (MockAPI returns the deleted object data).

e - Verify Required Properties & Types
Confirm the returned deleted object has all fields with correct types.

f - Data Consistency
Verify response matches request details (if a body was sent, though optional for DELETE).

g - Check Response Time
Ensure the API responds within 1000ms.

h - Environment Variable
Capture the ID from the response (although the item is deleted, the ID is returned).
========================================================================================================================================================
using newman run the collection 
========================================================================================================================================================

👨‍💻 Author
**Ahmed El-Sharkawi**  
*Junior Test Automation Engineer*

🔗 [LinkedIn Profile](https://www.linkedin.com/in/ahmed-el-sharkawi/)
🔗 [GitHub Profile](https://github.com/Ahmed2015-22)
