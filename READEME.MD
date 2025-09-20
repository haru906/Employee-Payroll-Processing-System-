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

{
    "status": "Payroll processed successfully",
    "recordsProcessed": 5
}
###  GET /reports/{month}   &  GET /reports/{month}?empId

Request Example:

GET /reports/June   


Response:
The data is stored in the payroll_transactions table in the database,
[
  {
    "empId": 101,
    "name": "John Doe",
    "department": "IT",
    "grossSalary": 5000,
    "taxAmount": 750,
    "netSalary": 4250,
    "month": "June"
  }
]

 and the payroll report can also be downloaded as a CSV or JSON file
 from the /output-reports/ folder.
 
 empId,name,department,grossSalary,taxAmount,netSalary,month
101,John Doe,IT,5000,750,4250,June
102,Jane Smith,HR,4500,450,4050,June
103,Alan Brown,Finance,5500,660,4840,June
104,Eva Green,Sales,4000,320,3680,June
105,Raj Patel,IT,6000,900,5100,June
 
 #### Use Postman or curl to hit the endpoints:
GET http://localhost:8081/api/employees
POST http://localhost:8081/api/payroll
GET http://localhost:8081/api/reports/month
 