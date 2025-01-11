# Mysql 

Tags: [[Starting Point]] [[Mysql]] [[Penetration Testing]] [[Cybersecurity]] #Mysql


## Enumeration 

```bash
sudo nmap -sC -sV $target
```

### Install mysql

```bash
sudo apt install default-mysql-client
```

#### Get Help with mysql

```Bash
mysql --help
```

### Authentication 

SQL Servers authenticate with a username/password combitnation. Sometimes its not setup right.
In this case you can get in without using a password. We can try to log into the server with the root and no password. 

```bash
mysql -h {targert_ip} -u root
```

#### Mysql commands


```bash
SHOW databases; : Prints out the databases we can access.
USE {database_name}; : Set to use the database named {database_name}.
SHOW tables; : Prints out the available tables inside the current
database.
SELECT * FROM {table_name}; : Prints out all the data from the table {table_name}.
```

### SSL Error 
#SSLError

```bash
# If you get a ssl error use this command

mysql -h $target -u root --skip-ssl
```




