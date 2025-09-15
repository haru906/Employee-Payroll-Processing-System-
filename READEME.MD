# Employee Payroll Processing System 

##  Project Overview
This MuleSoft-based integration project automates the process of employee payroll generation. 
It fetches employee data from a MySQL database, applies tax rule, 
calculates payroll, generates reports (CSV/JSON), and exposes APIs for integration.

The system is designed with the following in mind:
- API-first approach with RAML design
- Batch processing for monthly payroll execution
- Secure handling of configuration and credentials
- Reusable and modular flow design
- Testing with MUnit
- Scheduled execution at month-end
---

### API Endpoints

###   GET '/employees'
- **Description**: Fetch all employee details.
- **Response Example**:
```json
[
  {
    "emp_id": 101,
    "name": "John Doe",
    "department": "IT",
    "base_salary": 5000
  }
]

###   POST '/payroll'

Processes payroll for all employee.

{
  "month": "August",
}
Response Example

[
  {
    "empId": 101,
    "name": "John Doe",
    "department": "IT",
    "grossSalary": 5000,
    "taxAmount": 750,
    "netSalary": 4250,
    "month": "August"
  }
]

###  GET /reports/{month}

Downloads the payroll report for a specific month.

Request Example:

GET /reports/August

Response:
The data is stored in the payroll_transactions table in the database,
 and the payroll report can also be downloaded as a CSV or JSON file
 from the /output-reports/ folder.
 
 #### Use Postman or curl to hit the endpoints:
GET http://localhost:8081/api/employees
POST http://localhost:8081/api/payroll
GET http://localhost:8081/api/reports/August
 