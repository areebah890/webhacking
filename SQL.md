# 🗄 SQL Injection – Task Breakdown

## 📝 Room Overview
The **SQL Injection (SQLi)** room taught me how attackers can exploit improperly sanitized input to manipulate a database. I learned techniques to detect, exploit, and mitigate SQL Injection vulnerabilities safely.

---

## 📌 Tasks & Learnings

### 1. Understanding SQL Injection
- **Task:** Learn what SQL Injection is and why it happens.  
- **Learning:** SQLi occurs when user input is directly used in SQL queries without proper validation or parameterization. This allows attackers to manipulate queries to read, modify, or delete database data.

---

### 2. Identifying Vulnerable Inputs
- **Task:** Test input fields or URL parameters for SQLi.  
- **Learning:** I looked for forms, login fields, search bars, or URL parameters. Common indicators include error messages, unexpected output, or application crashes when special characters are entered (like `'` or `"`)—signs that SQL queries are not properly sanitized.

---

### 3. Exploiting Basic SQLi
- **Task:** Attempt simple payloads to bypass authentication or reveal data.  
- **Learning:** Using payloads like:

'sql' OR '1'='1

I could bypass login forms or retrieve data. I learned that simple logic manipulation in queries can have big effects.

### 4. Extracting Data
- **Task:** Extract database information such as table names, column names, and data.
- **Learning:**  I practiced using techniques like:

UNION SELECT statements to combine queries

Commenting out the rest of the query with --

Enumerating tables using information_schema
This helped me safely retrieve test database contents in the lab.

## 5. Error-Based and Blind SQLi
- **Task:** Learn different types of SQLi: error-based and blind.
- **Learning:**

Error-based: Exploits database error messages to extract information.

Blind SQLi: Retrieves information indirectly when no error messages are displayed, often using IF conditions or timing techniques.

## 6. Defensive Measures
- **Task:** Learn how to prevent SQL Injection.
- **Learning:** Key defenses include:

Using prepared statements and parameterized queries.

Validating and sanitizing all user input.

Minimizing database permissions for application accounts.

Avoiding detailed error messages to prevent information disclosure.

## 🎯 Key Takeaways
SQL Injection is a critical web vulnerability that can compromise entire databases.

Detecting SQLi requires understanding both input behavior and database responses.

Exploitation can be performed safely in lab environments to learn impact.

Proper input handling, parameterized queries, and least privilege principles are essential for defense.
