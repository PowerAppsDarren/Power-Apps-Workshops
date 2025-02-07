# Full Project Schema 

## Car

- Year
- Make
- Model
- Color
- Tag
- VIN
- Notes
- CustomerID

## Customer

- FirstName
- LastName
- Phone
- Notes
- Email

## Inspection

- CarID
- StaffInspectorID
- CustomerID
- InspectionType
- ManagerID
- Notes
- Completed

## Staff (AppUser)

- IsManager
- UserEmail (M365)
- AlternateEmail
- FirstName
- LastName
- EntraID
- EmployeeID
- Image
- HRNotes
- ITNotes
- PIN
- OfficeLocation
- Department
- DepartmentID
- JobTitle
- ManagerEmail
- ManagerEntraID

## QuestionCategory

- SortOrder

## Question

- CategoryName
- SortOrder
- CategorySortOrder
- FullQuestionText

## Answer

-  QuestionID
-  Category
-  QuestionText
-  InspectionID
-  AnswerValue
-  AnswerLong




## Table: **Question**

Below is the inferred SharePoint schema for the **Question** table based on the provided ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each question.                                           | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | No                     | No                       | No                       | Short description or title of the question.                                    | None              | None                          |
| CategoryName          | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Name of the category this question belongs to.                                 | None              | None                          |
| SortOrder             | Numeric                   | 10                   | Yes                    | No                       | No                       | Order in which the question appears in a list or UI.                           | None              | Positive integer only         |
| CategorySortOrder     | Numeric                   | 10                   | Yes                    | No                       | No                       | Sort order specific to the category.                                           | None              | Positive integer only         |
| FullQuestionText      | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Full text of the question, providing additional details if needed.             | None              | None                          |


## Table: **QuestionCategory**

Below is the inferred SharePoint schema for the **QuestionCategory** table based on the provided ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each question category.                                   | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | No                     | No                       | No                       | The name or title of the question category.                                     | None              | None                          |
| SortOrder             | Numeric                   | 10                   | Yes                    | No                       | No                       | Order in which the category appears in lists or UI.                             | None              | Positive integer only         |

## Table: **Answer**

Below is the inferred SharePoint schema for the **Answer** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each answer.                                              | None              | Must be unique, auto-increment|
| QuestionID            | Numeric                   | 18                   | No                     | No                       | Yes                      | Foreign key referencing the related question.                                   | None              | Must match an existing Question ID |
| Category              | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Category of the answer, if applicable.                                          | None              | None                          |
| QuestionText          | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Text of the related question for context.                                       | None              | None                          |
| InspectionID          | Numeric                   | 18                   | Yes                    | No                       | Yes                      | Foreign key referencing the related inspection.                                 | None              | Must match an existing Inspection ID |
| AnswerValue           | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Short text response or value for the answer.                                    | None              | None                          |
| AnswerLong            | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Detailed or extended response for the answer.                                   | None              | None                          |


## Table: **Inspection**

Below is the inferred SharePoint schema for the **Inspection** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each inspection.                                          | None              | Must be unique, auto-increment|
| CarID                 | Numeric                   | 18                   | No                     | No                       | Yes                      | Foreign key referencing the related car.                                        | None              | Must match an existing Car ID |
| StaffInspectorID       | Numeric                   | 18                   | Yes                    | No                       | Yes                      | Foreign key referencing the staff member performing the inspection.             | None              | Must match an existing Staff ID |
| CustomerID            | Numeric                   | 18                   | Yes                    | No                       | Yes                      | Foreign key referencing the customer associated with the inspection.            | None              | Must match an existing Customer ID |
| InspectionType        | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Type or category of the inspection.                                             | None              | None                          |
| ManagerID             | Numeric                   | 18                   | Yes                    | No                       | Yes                      | Foreign key referencing the manager overseeing the inspection.                  | None              | Must match an existing Staff ID |
| Notes                 | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Additional notes or details about the inspection.                               | None              | None                          |
| Completed             | Date Time                 | N/A                  | Yes                    | No                       | No                       | Date and time when the inspection was completed.                                | None              | None                          |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Foreign Key Indexes**:
  - `CarID` (to optimize joins with the Car table).
  - `StaffInspectorID` (to optimize queries involving staff inspectors).
  - `CustomerID` (to optimize joins with the Customer table).
  - `ManagerID` (to optimize joins with manager-related queries).
- **Search Index**: `InspectionType` (if filtering or searching by inspection type is frequent).


## Table: **Car**

Below is the inferred SharePoint schema for the **Car** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each car.                                                 | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | No                     | No                       | No                       | Name or title of the car (e.g., nickname or identifier).                        | None              | None                          |
| Year                  | Numeric                   | 4                    | Yes                    | No                       | No                       | Manufacturing year of the car.                                                  | None              | Must be a valid year value    |
| Make                  | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Manufacturer or brand of the car.                                               | None              | None                          |
| Model                 | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Model name or designation of the car.                                           | None              | None                          |
| Color                 | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Color of the car.                                                               | None              | None                          |
| Tag                   | Single Line of Text       | 255                  | Yes                    | No                       | No                       | License plate or tag number for the car.                                        | None              | None                          |
| VIN                   | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Vehicle Identification Number (VIN) for unique identification.                 | None              | Must be unique                |
| Notes                 | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Additional notes or details about the car.                                      | None              | None                          |
| CustomerID            | Numeric                   | 18                   | Yes                    | No                       | Yes                      | Foreign key referencing the customer associated with this car.                  | None              | Must match an existing Customer ID |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Foreign Key Index**: `CustomerID` (to optimize joins with the Customer table).
- **Search Indexes**:
  - `VIN` (to quickly locate cars by their unique VIN).
  - `Tag` (to optimize searches by license plate/tag number).

## Customer

Below is the inferred SharePoint schema for the **Customer** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each customer.                                            | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Title or reference name for the customer.                                       | None              | None                          |
| FirstName             | Single Line of Text       | 255                  | Yes                    | No                       | No                       | First name of the customer.                                                     | None              | None                          |
| LastName              | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Last name of the customer.                                                      | None              | None                          |
| Phone                 | Single Line of Text       | 50                   | Yes                    | No                       | No                       | Contact phone number for the customer.                                          | None              | Must be a valid phone number  |
| Notes                 | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Additional notes or details about the customer.                                 | None              | None                          |
| Email                 | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Email address of the customer.                                                  | None              | Must be a valid email address |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Search Indexes**:
  - `Email` (to optimize searches by email address).
  - `LastName` (to speed up queries involving customer names). 
