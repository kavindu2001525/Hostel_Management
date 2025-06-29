SANDEEPANI M.M.N. 
give me a readme file about my database

# Hostel Management System - Database

This database is designed for a Hostel Management System that manages student accommodation, room allocation, complaints, payments, visitor logs, and administrative roles.

## 📂 Database Name

`hostel_db`

## 📋 Tables Overview

### 1. `Admin`

Stores administrator credentials and personal details.

- `Admin_ID` (PK)

- `First_Name`, `Last_Name`, `Email`, `password`

### 2. `Warden`

Stores warden login and contact details.

- `Warden_ID` (PK)

- `First_Name`, `Last_Name`, `Email`, `password`, `Admin_ID` (FK)

### 3. `Student`

Stores student profile and room details.

- `Student_ID` (PK)

- `First_Name`, `Last_Name`, `Email`, `Room_Number` (FK), `Checkin_Date`, `Checkout_Date`, `Admin_ID` (FK), `Warden_ID` (FK)

### 4. `user`

Stores login information for students.

- `Student_ID` (PK)

- `First_Name`, `Last_Name`, `Email`, `password`

- ✅ Trigger: Automatically inserts into `Student` after registration.

### 5. `Room`

Stores information about each hostel room.

- `Room_Number` (PK)

- `Room_Type`, `AC_Type`, `Capacity`, `Occupied_Count`, `Admin_ID` (FK), `Warden_ID` (FK)

### 6. `Room_Request`

Tracks student room allocation requests.

- `Request_ID` (PK)

- `Student_ID` (FK), `Room_Number` (FK), `Status` (Pending/Approved/Rejected)

### 7. `Complaint`

Stores complaints submitted by students.

- `Complaint_ID` (PK)

- `Student_ID`, `Complaint_Type`, `Description`, `Office_Description`, `Status`, `Warden_ID`, `Admin_ID` (all FKs)

### 8. `Payment`

Tracks monthly hostel payments by students.

- `Payment_ID` (PK)

- `Student_ID` (FK), `Monthly_Rent`, `Payment_Day`, `Next_Pay_Day`, `Penalty_for_Late`, `Admin_ID` (FK)

### 9. `Visitor_Log`

Logs visitor details and warden approval.

- `Visitor_ID` (PK)

- `Student_ID` (FK), `Visit_Date`, `Visit_Time`, `Reason`, `Warden_Approval_Status`, `Warden_Disapproval_Reason`, `Warden_ID`, `Admin_ID` (FKs)

## 🔐 Foreign Key Relationships

- `Student → Room`, `Admin`, `Warden`

- `Complaint → Student`, `Admin`, `Warden`

- `Payment → Student`, `Admin`

- `Room → Admin`, `Warden`

- `Room_Request → Student`, `Room`

- `Visitor_Log → Student`, `Warden`, `Admin`

- `Warden → Admin`

## ⚙️ Triggers

- `insert_student_after_user`: Automatically adds a student record when a new user registers.

## 📌 Features Supported

- Single room request per student

- Room capacity check and update

- Complaint handling

- Visitor request with warden approval

- Secure user registration and login

---

This database is designed to ensure proper data integrity, normalization, and support for all key hostel management functions.
 
