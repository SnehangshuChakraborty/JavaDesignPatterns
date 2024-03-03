The concept of SRP (Single Responsiblity Principle) states that a class should have only one reason to change or in other words it should have only one job or responsiblity.

Consider following piece of code 

```java
package com.design.srp;

public class Employee {

    private String name;
    private String age;
    private double salary;

    public void saveEmployeeDetails() {
        //Some code to save employee details in database
    }

    public void generatePayroll() {
        //some code to generate payroll of employees
    }

    public void printEmployees() {
        //some code to generate the list of employees
    }

}
```

In this example the class Employee has multiple resposiblities
like
- Managing the employee data
- Generating payrolls
- Saving the employee data in the DB
- Printing reports

Based on the SRP principle this code would be refactored to something like this..

```java
// Employee class only represents employee data
public class Employee {

    private String name;
    private double salary;
    private String department;

    // Constructor, getters, and setters
}

// Class responsible for saving employee data to the database
public class EmployeeRepository {

    public void saveEmployee(Employee employee) {
        // Code to save employee details to the database
    }
}

// Class responsible for generating payroll for employees
public class PayrollGenerator {

    public void generatePayroll(Employee employee) {
        // Code to generate employee payroll
    }
}

// Class responsible for printing employee reports
public class EmployeeReportPrinter {

    public void printEmployeeReport(Employee employee) {
        // Code to print employee report
    }
}
```

If you look closely each class has just one responsibility and is doing just that.. 
This makes the overall code easier to understand, maintain and extend.