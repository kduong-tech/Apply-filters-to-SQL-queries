# Applying Filters to SQL Queries (Security Investigation)

This project is part of the Google Cybersecurity Professional Certificate. It demonstrates how SQL filtering techniques (AND, OR, NOT, LIKE, pattern matching, and date/time filtering) can be used to assist in security investigations involving authentication logs and employee data.

---

## 📄 Project Files
- Completed SQL filtering activity  
- SQL queries and screenshots  
- Scenario instructions  
- SQL formatting guidelines  

---

## 📝 Project Description
As a security professional at a large organization, I was tasked with investigating suspicious login activity and reviewing employee machine data. Using SQL, I analyzed the organization's `log_in_attempts` and `employees` tables by applying filters to retrieve relevant records. This work supported an active investigation into failed authentication attempts, geographic anomalies, and department-based security updates.  

---

# 🔍 SQL Tasks & Queries

Below are all six tasks from the activity **combined into one clean block**, each with the SQL query used and a short explanation.

---

## **🔹 Tasks
Identify **failed login attempts** that occurred **after 18:00**.

**Query:**
```sql
🔹 Task 1 — After-Hours Failed Login Attempts**
Identify **failed login attempts** that occurred **after 18:00**.
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00'
  AND success = 0;

🔹 Task 2 — Login Attempts on Specific Dates

Retrieve logins from 2022-05-08 OR 2022-05-09.

Query:

SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-08'
   OR login_date = '2022-05-09';


Why it works:

Uses OR to match either of the two dates involved in the investigation

🔹 Task 3 — Login Attempts Outside of Mexico

Investigate login attempts NOT originating in Mexico.

Query:

SELECT *
FROM log_in_attempts
WHERE country NOT LIKE '%MEX%';


Why it works:

LIKE '%MEX%' detects both MEX and MEXICO

NOT excludes all of them

🔹 Task 4 — Employees in Marketing (East Building)

Retrieve Marketing employees in any East-building office.

Query:

SELECT *
FROM employees
WHERE department LIKE '%Marketing%'
  AND office LIKE 'East%';


Why it works:

LIKE '%Marketing%' catches “Marketing” even if part of a longer string

LIKE 'East%' ensures the office number begins with “East-“

🔹 Task 5 — Employees in Finance OR Sales

Identify employees in Finance OR Sales.

Query:

SELECT *
FROM employees
WHERE department LIKE '%Finance%'
   OR department LIKE '%Sales%';


Why it works:

Uses OR to capture multiple departments

LIKE handles any variations in wording

🔹 Task 6 — Employees NOT in IT

Retrieve all employees not in the IT department.

Query:

SELECT *
FROM employees
WHERE department NOT LIKE '%Information Technology%';
