Tags: [[SQL Injection]] [[Penetration Testing]] [[Cybersecurity]]

### **What is SQL?**

**SQL (Structured Query Language)** is a standard programming language used to manage and manipulate relational databases. It allows users to perform tasks such as querying data, updating records, inserting new data, and deleting data within relational databases.

SQL is used with systems like:
- **MySQL**
- **PostgreSQL**
- **Microsoft SQL Server**
- **SQLite**
- **Oracle DB**

### **Basic SQL Commands**

1. **SELECT** – Retrieves data from a database:
   ```sql
   SELECT * FROM users;
   ```

2. **INSERT** – Adds new data into a table:
   ```sql
   INSERT INTO users (username, password) VALUES ('admin', 'password123');
   ```

3. **UPDATE** – Modifies existing data:
   ```sql
   UPDATE users SET password = 'newpassword' WHERE username = 'admin';
   ```

4. **DELETE** – Removes data from a table:
   ```sql
   DELETE FROM users WHERE username = 'admin';
   ```

5. **CREATE** – Defines a new table, database, or index:
   ```sql
   CREATE TABLE users (id INT PRIMARY KEY, username VARCHAR(50), password VARCHAR(50));
   ```

6. **DROP** – Deletes a table or database:
   ```sql
   DROP TABLE users;
   ```

---

### **SQL Penetration Testing Overview**

Penetration testing of SQL-based systems involves identifying vulnerabilities in database management systems (DBMS) and exploiting them to gain unauthorized access, escalate privileges, or retrieve sensitive information. Key areas to focus on include **SQL injection**, **authentication flaws**, **privilege escalation**, and **misconfigurations**.

---

### **Common SQL Vulnerabilities to Test**

#### **1. SQL Injection (SQLi)**

**SQL Injection** is one of the most common vulnerabilities, where the attacker manipulates SQL queries by injecting malicious SQL code through input fields.

**Types of SQL Injection**:
- **In-band SQL Injection (Classic SQLi)**: Attacker uses the same channel for both the attack and the result.
- **Blind SQL Injection**: Attack occurs without visible error messages. The attacker guesses the response based on true/false answers.
- **Out-of-band SQL Injection**: Data is retrieved using different channels, such as DNS requests or HTTP requests.

**SQL Injection Test Examples**:

1. **Basic SQLi**:
   - If a website has a login form, attempt entering `' OR 1=1 --` as the username or password to bypass authentication.
     ```sql
     SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = '';
     ```

2. **Boolean-based Blind SQLi**:
   - Modify input like `admin' AND 1=1 --` or `admin' AND 1=2 --` to check if the application responds differently based on true/false conditions.

3. **Union-based SQLi**:
   - Use the `UNION` operator to combine results from different queries and retrieve database information:
     ```sql
     ' UNION SELECT null, username, password FROM users --
     ```

4. **Time-based Blind SQLi**:
   - Inject queries that cause the database to delay the response, indicating the query is executing. For example, adding `SLEEP(5)` to delay the response for 5 seconds.

#### **2. Privilege Escalation**

Test for vulnerabilities where users may gain elevated privileges.

- **Bypassing Authentication**: Test if unauthorized users can gain admin rights by manipulating `user` and `password` fields (e.g., `admin' --` to bypass login checks).
- **Exploiting Misconfigured Permissions**: Check if users can query sensitive data or perform administrative actions they shouldn't have access to.

#### **3. Information Disclosure**

Check if the SQL errors are too verbose, revealing sensitive information such as:
- Database version (`mysql -V`)
- Table names and structures
- Stack traces or error messages exposing sensitive data

Example error:
```sql
ERROR: Column 'username' not found in the field list
```

#### **4. Authentication Bypass**

- **No Password/Weak Passwords**: Try using common or weak passwords (like `admin`, `password123`, `root`) to see if they work.
- **Stored Procedures**: Check for poorly configured stored procedures that allow unauthorized users to execute system-level operations.

#### **5. Insecure Database Configuration**

- **Exposed Admin Interface**: Check if the database's administrative interface is exposed to the internet without proper authentication.
- **Default Database Credentials**: Test for default credentials like `root:root`, `admin:admin`, etc.
- **Backup Files**: Search for backup files (`.bak`, `.sql`, `.tar`) that may contain sensitive data. You can do this using commands like `find` on the server or `dir` in a web directory.

#### **6. Error-Based SQL Injection**

- **Database Errors**: Look for detailed error messages that might expose the structure of the database, table names, column names, etc. Test for errors like:
  - `MySQL error code 1064`
  - `PostgreSQL error: syntax error`

---

### **Penetration Testing Tools for SQL**

1. **SQLMap** – An automated tool to detect and exploit SQL injection vulnerabilities:
   ```bash
   sqlmap -u "http://target.com/page?id=1" --batch --risk=3 --level=5
   ```

2. **Burp Suite** – A web vulnerability scanner with SQL injection detection.
   - Use the **Intruder** and **Scanner** features to test for SQLi.

3. **Nikto** – A web scanner that can identify database misconfigurations.
   ```bash
   nikto -h http://target.com
   ```

4. **Havij** – An automated SQL injection tool designed for penetration testers.

5. **OWASP ZAP** – A security scanner that helps find SQLi vulnerabilities and other web app issues.

---

### **Mitigation of SQL Vulnerabilities**

1. **Prepared Statements (Parameterized Queries)** – Prevent SQL injection by using parameterized queries instead of dynamic queries. In most modern languages, this can be done as:
   ```python
   cursor.execute("SELECT * FROM users WHERE username = %s AND password = %s", (username, password))
   ```

2. **Stored Procedures** – Use stored procedures instead of inline SQL commands. Ensure that stored procedures do not accept user inputs directly.

3. **Least Privilege Principle** – Limit database user privileges to the bare minimum. Users should only have access to what they need.

4. **Input Validation** – Validate and sanitize all user inputs, especially those that will be used in SQL queries. Use whitelisting and reject invalid characters.

5. **Error Handling** – Implement proper error handling to prevent detailed error messages from being exposed. For example, use generic error messages like:
   - `"An error occurred. Please try again later."`
   - Avoid exposing stack traces.

6. **Database Configuration** – Disable unnecessary database features, and ensure that the database is not exposed directly to the internet.

---

### **Key SQL Penetration Testing Steps**

1. **Reconnaissance**:
   - Identify and map out any publicly exposed databases or web apps.
   - Check for open ports related to SQL (default: 3306, 5432, 1433, etc.).

2. **Scanning**:
   - Use tools like **Burp Suite**, **SQLMap**, or **Nikto** to scan for SQL vulnerabilities.
   - Manually test input fields with common SQLi payloads.

3. **Exploitation**:
   - Exploit identified SQL injection vulnerabilities to extract data, escalate privileges, or compromise the system.

4. **Post-Exploitation**:
   - Extract sensitive data like user information, passwords, and configuration details.
   - Check for access to other systems or privileges that may lead to further exploitation.

---

