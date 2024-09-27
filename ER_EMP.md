
```mermaid
erDiagram
    USER {
        int id PK
        string username
        string password
        string role
    }
    ADMIN {
        string adminCode PK
        string fullName
        string email
        string phoneNumber
    }
    EMPLOYEE {
        string employmentCode PK
        string fullName
        date dateOfBirth
        string gender
        int age
        string personalEmail
        string companyEmail
        string mobileNumber
        date dateOfJoining
        string reportingManagerCode FK
    }
    PERSONAL_DETAILS {
        string employmentCode FK
        string currentAddress
        string permanentAddress
        string emergencyContactName
        string emergencyContactMobile
    }
    PROFESSIONAL_DETAILS {
        string employmentCode FK
        string officePhone
        string city
        string officeAddress
        string hrName
    }
    EMPLOYMENT_HISTORY {
        int id PK
        string employmentCode FK
        string companyName
        date joinDate
        date endDate
    }
    PROJECT {
        string projectCode PK
        string clientName
        string projectManagerCode FK
    }
    EMPLOYEE_PROJECT {
        int id PK
        string employmentCode FK
        string projectCode FK
        date startDate
        date endDate
    }
    FINANCE {
        string employmentCode FK
        string panCard
        string aadharCard
        string bankName
        string branchName
        string ifscCode
    }
    PAYSLIP {
        int id PK
        string employmentCode FK
        date payslipDate
        string pdfUrl
    }
    CTC_BREAKUP {
        int id PK
        string employmentCode FK
        string componentName
        decimal amount
    }

    USER ||--o{ EMPLOYEE : "has"
    USER ||--o{ ADMIN : "has"
    ADMIN ||--o{ EMPLOYEE : "manages"
    ADMIN ||--o{ PROJECT : "manages"
    EMPLOYEE ||--|| PERSONAL_DETAILS : "has"
    EMPLOYEE ||--|| PROFESSIONAL_DETAILS : "has"
    EMPLOYEE ||--o{ EMPLOYMENT_HISTORY : "has"
    EMPLOYEE ||--o{ EMPLOYEE_PROJECT : "assigned to"
    PROJECT ||--o{ EMPLOYEE_PROJECT : "has"
    EMPLOYEE ||--|| FINANCE : "has"
    EMPLOYEE ||--o{ PAYSLIP : "has"
    EMPLOYEE ||--o{ CTC_BREAKUP : "has"
