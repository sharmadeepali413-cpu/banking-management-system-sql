# 🏦 Banking Management System – SQL Project

A complete **banking database project** built with **MySQL**. It covers database design (ER diagram), data loading from CSV files, and **35 real-world SQL business questions** on security, customers, employees, loans and fraud detection.

---

## 📌 Project Overview

This project shows how a bank stores and manages its data: customers, accounts, transactions, loans, employees, branches, and user access (roles & permissions). After building the database, I wrote SQL queries to answer business questions that a data analyst or auditor would ask.

**Goal:** Practice database design, joins, subqueries, CTEs, window functions and data-quality checks on a realistic banking dataset.

---

## 🛠️ Tools & Technologies

| Tool | Use |
|------|-----|
| MySQL / MySQL Workbench | Database creation & SQL queries |
| CSV files | Source data loaded into MySQL |
| MySQL Workbench EER Diagram (`main.mwb`) | Database design |

---

## 🗂️ Database Schema

**Database name:** `bank_managment_system`

**12 tables:**

| Area | Tables |
|------|--------|
| Access control | `roles`, `permissions`, `role_permissions`, `users` |
| Bank setup | `branches`, `employees` |
| Customers & accounts | `customers`, `accounts`, `transactions` |
| Loans | `loans`, `loan_payments` |
| Security | `audit_logs` |

### Dataset size

| Table | Rows (approx.) |
|-------|----------------|
| customers | 1,000 |
| accounts | 1,000 |
| employees | 1,000 |
| users | 1,000 |
| loans | 1,000 |
| transactions | ~2,950 |
| loan_payments | ~3,030 |
| audit_logs | ~2,000 |
| branches | 50 |
| roles / permissions / role_permissions | 5 / 5 / 16 |

> ⚠️ All data is **sample / dummy data** created for learning. It does not belong to any real person or bank.

### Relationships (short)
- `users` → `employees`, `roles`
- `employees`, `accounts`, `loans` → `branches`
- `accounts`, `loans` → `customers`
- `transactions` → `accounts`, `users`
- `loan_payments` → `loans`
- `audit_logs` → `users`

(See the ER model in `design/main.mwb`, open it with MySQL Workbench.)

---

## 📁 Repository Structure

```
banking-management-system-sql/
│
├── README.md
├── SQL_Projects_Question.docx      # 35 business questions
├── sql/
│   └── bank.sql                    # Create tables + all solutions
├── data/
│   ├── Accounts.csv
│   ├── Audit_logs.csv
│   ├── Branches.csv
│   ├── Customers.csv
│   ├── Employes.csv
│   ├── Loan_payments.csv
│   ├── loans_1000_records.csv
│   ├── loans.csv                   # extra loan dataset (200 rows, credit details)
│   ├── Permissions.csv
│   ├── Role_Permissions.csv
│   ├── roles.csv
│   ├── Transactions.csv
│   └── Users.csv
└── design/
    └── main.mwb                    # MySQL Workbench ER model
```

---

## ▶️ How to Run This Project

1. Install **MySQL Server** and **MySQL Workbench**.
2. Open `sql/bank.sql` and run the `CREATE TABLE` part (creates database `bank_managment_system` and all tables).
3. Import the CSV files from the `data/` folder using **Table Data Import Wizard**.
   Import in this order (because of foreign keys):
   `roles → permissions → role_permissions → branches → employees → users → customers → accounts → transactions → loans → loan_payments → audit_logs`
4. Run the query solutions one by one and check the output.

> Note: Some CSV files use `;` (semicolon) as separator. Choose the correct separator while importing.
> In `Employes.csv`, some phone numbers are in Excel scientific format (e.g. `9.1043E+11`), so they fail the phone-format check (question 27). This is a data-quality issue the query detects.

---

## ❓ SQL Business Questions Solved (35)

### 🔐 Roles, Permissions & Access Control
1. Identify users who have all permissions in the system
2. List users whose roles have conflicting permissions (Approve Loan vs Reject Loan)
3. List users with permissions but no assigned role
4. Identify roles that are subsets of other roles
5. Find users with overlapping permissions from multiple roles
6. Identify users whose role permissions changed in the last 30 days (via `audit_logs`)
7. Detect permissions assigned to only a single user
8. Detect permissions assigned to inactive users
9. Find roles that have at least one permission not assigned to any user

### 👥 Customers & Accounts
10. Top 5 customers whose total balance across accounts exceeds 10 lakh
11. Customers with accounts in multiple branches
12. Accounts with no deposits in the last 6 months
13. Customers whose accounts were frozen and later reopened
14. Average balance growth per customer per month
15. Customers whose balance decreased for 3 consecutive months
16. Accounts never used for any transaction
17. Accounts opened on weekends or holidays
18. Customers with duplicate `national_id` (data anomaly)

### 🏢 Branches & Employees
19. Branches where no employee performed a transaction in the last month
20. Employees managing accounts across multiple branches
21. Employees with the highest number of loan approvals
22. Employees hired but never assigned to a branch
23. Employees with overlapping account management responsibilities
24. Duplicate branch locations (data cleaning)
25. Employees handling high-value transactions (> 5 lakh) without authorization
26. Branches with highest customer balance but fewest employees
27. Employees whose email/phone violates format rules (data validation)

### 💰 Loans
28. Loans pending approval for more than 90 days
29. Customers with multiple overlapping loans exceeding credit limit
30. Loans with no payment after the due date
31. Effective interest rate per customer considering partial payments
32. Loans approved but never disbursed

### 🚨 Fraud & Audit
33. Users who performed actions on accounts/loans they don't own
34. Users performing more than 50 actions in 1 hour (possible fraud)
35. All transactions linked to users flagged in `audit_logs`

---

## 💡 SQL Concepts Used

- `INNER JOIN`, `LEFT JOIN`, self joins
- `GROUP BY`, `HAVING`, aggregate functions
- Subqueries & CTEs
- Window functions (`LAG`)
- Date functions (`DATEDIFF`, `DATE_SUB`, `DAYOFWEEK`)
- Data validation with `REGEXP`
- Primary keys, foreign keys, `ENUM`, constraints

---

## 🔍 Key Learnings

- Designing a normalized banking database with proper relationships
- Writing complex multi-table queries for real business problems
- Finding data-quality problems (duplicates, wrong formats)
- Basic fraud and audit analysis using SQL

---

## 🚀 Future Improvements

- Build a **Power BI dashboard** on top of this database
- Add an **Excel dashboard** (pivot tables & charts) connected to MySQL
- Add stored procedures and triggers for automatic audit logging
- Add indexes and check query performance

---

## 👩‍💻 Author

**Deepali Sharma**
Aspiring Data Analyst | SQL • Advanced Excel • Power BI • Python
📍 Ghaziabad, Uttar Pradesh, India

🔗 LinkedIn: [https://www.linkedin.com/in/your-linkedin-deepali-sharma-689731340/](https://www.linkedin.com/in/deepali-sharma-689731340/)

💻 GitHub: [https://github.com/your-github-sharmadeepali413-cpu](https://github.com/sharmadeepali413-cpu)

⭐ If you like this project, please give it a star!
