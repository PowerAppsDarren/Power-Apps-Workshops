# Full Project Schema 

```Text
Question
QuestionCategory
Answer
Inspection
Car
Customer
Staff
AppUser
AppPreference
AppUserPreference
AppSetting
Application
AppRole
AppUserRole
```



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


## Staff

Below is the inferred SharePoint schema for the **Staff** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each staff member.                                        | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Title or position of the staff member.                                          | None              | None                          |
| IsManager             | Yes/No                   | N/A                  | Yes                    | No                       | No                       | Indicates whether the staff member is a manager.                                | No                | None                          |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Search Index**: `IsManager` (to optimize queries filtering by managerial status).


## AppUser

Below is the inferred SharePoint schema for the **AppUser** table, focusing on the first 10 columns.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each application user.                                    | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Title or role of the application user.                                          | None              | None                          |
| UserEmail             | Single Line of Text       | 255                  | No                     | No                       | No                       | Email address of the application user.                                          | None              | Must be a valid email address |
| AlternateEmail        | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Alternate email address for the user.                                           | None              | Must be a valid email address |
| FirstName             | Single Line of Text       | 255                  | Yes                    | No                       | No                       | First name of the user.                                                         | None              | None                          |
| LastName              | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Last name of the user.                                                          | None              | None                          |
| EntryID               | Numeric                   | 18                   | Yes                    | No                       | No                       | Internal entry ID for tracking purposes.                                        | None              | None                          |
| EmployeeID            | Numeric                   | 18                   | Yes                    | No                       | No                       | Employee identifier for HR or payroll systems.                                  | None              | Must be unique                |
| PhotoBase64           | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Base64-encoded string representing the user's profile photo.                    | None              | None                          |
| HRNotes               | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Notes related to HR or personnel management for the user.                       | None              | None                          |
| ITNotes               | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | Notes related to IT or technical support for the user.                          | None              | None                          |
| PIN                   | Single Line of Text       | 50                   | Yes                    | No                       | No                       | Personal Identification Number for user authentication.                         | None              | Must be numeric               |
| OfficeLocation        | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Office location or address for the user.                                        | None              | None                          |
| Department            | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Department to which the user belongs.                                           | None              | None                          |
| JobTitle              | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Job title or position of the user.                                              | None              | None                          |
| ManagerEmail          | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Email address of the user's manager.                                            | None              | Must be a valid email address |
| PhotoBase64Length     | Numeric                   | 18                   | Yes                    | No                       | No                       | Length of the Base64-encoded photo string, if applicable.                       | None              | Must be positive integer      |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Search Indexes**:
  - `UserEmail` (to optimize searches by email).
  - `EmployeeID` (to quickly locate users by employee ID).
  - `PIN` (to optimize searches by user PIN).
  - `ManagerEmail` (to optimize queries involving managers).
  - `Department` (to optimize filtering by department).





## AppPreference

Below is the inferred SharePoint schema for the **AppPreference** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each application preference.                              | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | No                     | No                       | No                       | Name or title of the preference.                                                | None              | None                          |
| DataType              | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Data type of the preference value (e.g., string, number).                       | None              | None                          |
| SortOrder             | Numeric                   | 10                   | Yes                    | No                       | No                       | Order in which the preference appears in lists or UI.                           | None              | Positive integer only         |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Search Indexes**:
  - `Title` (to optimize searches by preference name).
  - `SortOrder` (to optimize sorting operations).


## AppUserPreference

Below is the inferred SharePoint schema for the **AppUserPreference** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each user preference entry.                               | None              | Must be unique, auto-increment|
| AppUserID             | Numeric                   | 18                   | No                     | No                       | Yes                      | Foreign key referencing the related user in the AppUser table.                  | None              | Must match an existing AppUser ID |
| AppPreferenceID       | Numeric                   | 18                   | No                     | No                       | Yes                      | Foreign key referencing the related preference in the AppPreference table.       | None              | Must match an existing AppPreference ID |
| Answer                | Multi-Line Text           | Unlimited             | Yes                    | No                       | No                       | User's answer or value for the specified preference.                            | None              | None                          |
| AppID                 | Numeric                   | 18                   | Yes                    | No                       | Yes                      | Foreign key referencing the related application in the Application table.        | None              | Must match an existing Application ID |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Foreign Key Indexes**:
  - `AppUserID` (to optimize joins with the AppUser table).
  - `AppPreferenceID` (to optimize joins with the AppPreference table).
  - `AppID` (to optimize joins with the Application table).


## AppSetting

Below is the inferred SharePoint schema for the **AppSetting** table based on the ERD diagram.

| **Column Name**       | **SharePoint Field Type** | **Length/Precision** | **Nullable (Yes/No)** | **Primary Key (Yes/No)** | **Foreign Key (Yes/No)** | **Description**                                                                 | **Default Value** | **Constraints**               |
|------------------------|---------------------------|-----------------------|------------------------|--------------------------|--------------------------|---------------------------------------------------------------------------------|-------------------|-------------------------------|
| ID                    | Numeric                   | 18                   | No                     | Yes                      | No                       | Unique identifier for each application setting.                                 | None              | Must be unique, auto-increment|
| Title                 | Single Line of Text       | 255                  | No                     | No                       | No                       | Name or title of the setting.                                                   | None              | None                          |
| DataType              | Single Line of Text       | 255                  | Yes                    | No                       | No                       | Data type of the setting value (e.g., string, number).                          | None              | None                          |
| SortOrder             | Numeric                   | 10                   | Yes                    | No                       | No                       | Order in which the setting appears in lists or UI.                              | None              | Positive integer only         |
| AppID                 | Numeric                   | 18                   | Yes                    | No                       | Yes                      | Foreign key referencing the related application in the Application table.        | None              | Must match an existing Application ID |

### Recommended Indexes
- **Primary Key Index**: `ID` (to ensure uniqueness and fast lookups).
- **Foreign Key Index**: `AppID` (to optimize joins with the Application table).
- **Search Indexes**:
  - `Title` (to optimize searches by setting name).
  - `SortOrder` (to optimize sorting operations).
