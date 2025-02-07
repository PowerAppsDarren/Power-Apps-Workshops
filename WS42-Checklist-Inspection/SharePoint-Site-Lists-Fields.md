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

