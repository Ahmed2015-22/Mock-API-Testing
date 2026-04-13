# 🚀 Mock API Testing – Postman & Newman

This repository demonstrates a professional **API Testing Workflow** using **Postman** for automated validation and **Newman** for command-line execution and reporting.

The project covers a complete CRUD lifecycle for an Employee Management System, ensuring data integrity, schema validation, and performance benchmarks.

## 🔗 Quick Links
- **API Documentation (MockAPI):** [https://mockapi.io/](https://mockapi.io/)
- **Base URL:** `https://697f9730d1548030ab667629.mockapi.io/`

> 💡 **Note:** Test data is dynamically handled and environment variables are updated during execution to ensure test reliability and repeatability.

---

## 🛠 Tools & Technologies
* **Postman:** For collection development and test scripting.
* **Newman:** To run collections via CLI.
* **Node.js:** Runtime environment.
* **Newman-Reporter-Htmlextra:** For generating detailed visual HTML reports.
* **JavaScript:** Used for writing custom test scripts and assertions.

---

## 🧪 Test Scenarios Overview

Each request includes a suite of automated tests covering:

### 1. GET All Employees
- **Status Code:** Verify `200 OK`.
- **Performance:** Response time must be `< 800ms`.
- **Structure:** Validate response is a JSON Array and not empty.
- **Data Integrity:** Check unique IDs and validate data types (String, Number, Boolean).
- **Business Logic:** Validate salary ranges ($0 - $1,000,000) and phone number formats.
- **Schema Validation:** Strict check for required fields (`id`, `name`, `phone`, `salary`, `married`).

### 2. GET Single Employee
- **Path:** `/employee/:id`
- **Logic:** Verify the returned ID matches the requested parameter.
- **Automation:** Captures the `id` from the response and stores it as an **environment variable** (`employeeId`) for downstream requests.

### 3. CREATE New Employee (POST)
- **Status Code:** Verify `201 Created`.
- **Validation:** Confirm all sent properties are correctly saved and returned in the response.
- **Persistence:** Automatically updates the `employeeId` variable to ensure subsequent Update/Delete tests target the newly created record.

### 4. UPDATE & EDIT (PUT / PATCH)
- **Data Consistency:** Parses the Request Body and compares it directly with the Response Body to ensure the server accurately reflects changes.
- **Schema Compliance:** Validates that the full object remains intact and valid after partial updates.
- **Headers:** Ensures `Content-Type: application/json` is returned.

### 5. DELETE Employee
- **Status Code:** Verify successful deletion (`200 OK`).
- **Post-Condition:** Validates that the response returns the deleted object data for confirmation.

---

## 🚀 Execution & Reporting

To run this collection locally, ensure you have **Newman** installed, then use the following commands:

### 1. Install Reporters (Optional)
```bash
npm install -g newman-reporter-htmlextra
```
2. Run the Collection
========================================================================================================================================================
using newman run the collection
cmd: newman run coll_name.json -e env_name.json -r htmlextra
========================================================================================================================================================

👨‍💻 Author
**Ahmed El-Sharkawi**  
*Junior Test Automation Engineer*

🔗 [LinkedIn Profile](https://www.linkedin.com/in/ahmed-el-sharkawi/)
🔗 [GitHub Profile](https://github.com/Ahmed2015-22)
