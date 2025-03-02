# Birth-Records-Analysis
This project involves analyzing birth records using SQL. The dataset consists of birth records, hospitals, doctors, maternal health data, and birth types. The analysis aims to uncover insights such as birth trends by region, doctor-specific deliveries, and birth type frequencies. This repository contains SQL scripts, database schema, queries, ERD diagrams, and screenshots of the results.

    Key Objectives 

1. Identify hospitals with the most birth records
2. Analyze doctors and their number of deliveries
3. Understand birth trends by birth type and region
4. Investigate mental health condition

   



## Database Structure 📊

| **Table**       | **Description**  |
|---------------|----------------------------------------------|
| **Birth_Record** | Stores birth events and links to doctors, hospitals, and birth types. |
| **Doctor**  | Contains doctor names and specializations. |
| **Hospital**  | Information about hospitals where births occur. |
| **Birth_Type**  | Types of births (e.g., Natural, C-Section, Water Birth). |
| **Mother**  | Maternal health data, including health conditions. |
| **Region**  | Locations linked to mothers and hospitals. |

## Business Rules ⚖️

- Each birth record is linked to **one hospital**.
- Each doctor can oversee **multiple births**, but one birth is attended by **one doctor**.
- A birth must have **an assigned birth type**.
- Each mother is associated with **a single region**.
- Regions can have **multiple hospitals and doctors**.
- **One hospital** can have many birth records.
- **One birth type** can apply to multiple birth records.
- **One mother** can have only one birth record.

 ## SQL Queries used

  ### **Identify hospitals with the highest birth records**
```sql
SELECT Hospital.Hospital_ID, Hospital.Name, COUNT(Birth_Record.Birth_ID) AS Total_Births
FROM Birth_Record
JOIN Hospital ON Birth_Record.Hospital_ID = Hospital.Hospital_ID
GROUP BY Hospital.Hospital_ID, Hospital.Name
ORDER BY Total_Births DESC;
📷 See results: hospital_births_query

### **Analyze doctors and their number of deliveries**
```sql
SELECT Doctor.Doctor_ID, Doctor.Name, COUNT(Birth_Record.Birth_ID) AS Total_Deliveries
FROM Birth_Record
JOIN Doctor ON Birth_Record.Doctor_ID = Doctor.Doctor_ID
GROUP BY Doctor.Doctor_ID, Doctor.Name
ORDER BY Total_Deliveries DESC;
📷 See results: doctor_deliveries 

   
