The intention of SQL injection is to reveal or manipulate sensitive information from the database by injecting 
commands into existing queries.

- Bypassing authentication
- Revealing sensitive information
- Compromise data integrity
- Erease database
- Remote code execution

**Tool** :

- sqlmap

# SQL

SQL stands for **S**tructured **Q**uery **L**anguage.

SQL tutorial [here](https://www.w3schools.com/sql/sql_delete.asp)

# Types of SQL Injection

## In-Band SQL Injection

Use the same communication channel to launch the attack and get the result.

### Error Based SQL Injection

- Server throw an error message
- Error meesage is useful during the developement, but should be disabled it when the application is live

#### Techniques to perform SQL Injection

- System stored procedure
- End of line comment
- Illegal / Logically incorrect query
- Tautology (something that is inherently true, like " OR 1=1")

### Union SQL Injection

Involves the UNION SQL operator, to combine the queries.

Select the `password` from `table1` and `table2` using UNION:

```
SELECT password FROM table1
UNION
SELECT password FROM table2
```

## Inferential SQL Injection

- Known as **Blind SQL Injection**
- No data is transferred from the via the application, the attacker sending payloads, then observe the web apllication's response and behaviour.

### Boolean-based Blind SQL Injection

Sending an SQL query to the database which send a different result depending on whether the query returns TRUE 
or FALSE result, the HTTP response will change or remain the same.

This type of attack is slow, attacker need to enumerate the database, character by character.

### Time-based Blind SQL Injection

Attacker send a query, force the database to wait for a specified time before respond.
The respond time indicate that the query TRUE or FALSE.

## Out-of-band SQL Injection

Depends on the features allowed on the database server (DNS, HTTP request), so not a very common attack. 

Use different channel to launch the attack. 

# SQL Injection Methodology

## Information Gathering And Vulnerability Detection

- Collect the information about the web application, server, OS, database, ...
- Identify vulnearbilities 
- Evaluate input fields

## Launch Attack

- Select the appropriate type of SQL Injection, based on the gathered information

## Advanced SQL Injection

- Enumarte the database (Postgre, MySQL, Oracle, ...)
- Identify privilege level of users
- Passwords and hashes grabbing
- Transfer database to a remote machine

# Evasion Techniques 

## Evading IDS

- Inserting inline comment in betweeen keywords
- Character encoding
- String Concatenation
- Obfuscated codes
- Manipulating white spaces
- Hex encoding
- Sophisticated matches

# Countermeasures

- Penetration testing (manual, with tool)
- Source code analysis
- Wep Application Firewall (WAF)
- Remove deugging messages
- Database account with minimal privileges
- Input validation
- Filter data
- Customize error messages
- IDS
