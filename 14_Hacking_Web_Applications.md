**Web Applications** are that applications that is running on a remote application server and avaliable for 
clients over the internet.

**Server Administrators** are resposible for the web server's safety, speed, functioning and performance.

**Application Administrators** are responsible for the management and configuration required for the web 
application.

**Clients** are the endpoints which interact with the web application / server.

# How Web Applications work?

**Front-end** <-> **Back-end**

Users are interacting with the front-end.
The processing was controlled and processed by the back-end.

Server-side languages:

- PHP
- Java
- C#
- Python
- JavaScript
- many more...

Client-side languages:

- CSS
- JavaScript
- HTML

#### Layers of Web Applications

- **Presentation Layer** is responsible for displaying the information to the user.
- **Logical Layer** : manipulate information to and from the forms. 
- **Data Layer** : hold the data for the application.

#### Web 2.0

In web 1.0, the users are limited to passive viewing the content.

In web 2.0, the users can interact and collaborate, it contain rich user experience, dynamic content.

# Web Application Threats

- Cookie poisoning
- Insecure storage
- Information leakage
- Directory traversal
- Parameter/Form tampering
- DOS attack
- Buffer overflow
- Log tampering
- SQL injection
- Cross-site Script
- Cross-site Request Forgery
- Security misconfiguration
- Broken session management
- DMZ attacks
- Session hijacking
- Network access attacks

#### Unvalidated input

Process an non-validated input from the client to the back-end. This is a major vulnerability, this is the 
basics of injection attacks (SQL injection, xss, buffer overflow).

#### Parameter / Form Tanmpering

Parameter tempering is an attack, where the attacker manipulate the parameter while client and server are 
communicating with each other. Parameters such as **Uniform Resource Locator** (URL) or web page form fields 
are modified (cookies, HTTP Header, form fields). 

#### Injection Flaws

Works if a web application allows untrusted input to be executed.

- Malicious code injection
- File injection
- SQL injection
- Command injection
- LDAP injection

#### SQL Injection

Injection of malicious SQL queries.
Attacker can manipulte the database
These vulnerabilities can be detected by using an automated scanner.

#### Command Injection

- Shell injection
- File injection
- HTML embedding

#### LDAP Injection

Attacker can access the database using LDAP filter to search information.

#### DoS Attack

- **User Registartion DoS** : an automated process, the attacker keep registering fake accounts. 
- **Login DoS** : attacker keep sending login requests.
- **User Enumeration** : attacker brute force login credebtials with a dictionary attacks.
- **Account Lock** : attacker attempt to lock the user account by attempting invalid passwords.

# Web Application Hacking Methodology

## Analyze Web Application

- Observing functionality
- Identify vulnerabilities, entry points, servers
- HTTP request analyze
- HTTP fingerprinting
- Hidden content discovery

## Attack Authentication

Exploit the authentication mechanism:

- Username enumerate
- Cookie exploitation
- Session attacks
- Password attacks

#### Authorization Attack Schemes

- Accessing the web application with low level privilege account, then escalate privileges to get information
- Parameter tampering (URL, POST data, Query string, cookies, HTTP header)

#### Session Management Attack

Impersonate a legitimate user.

Session hijacking techniques:

- Session token prediction
- Sessionn token tampering
- Man-in-the-Middle attack
- Session replay

#### Injection Attacks

Inject malicious code, commands and files.

Techniques:

- Web Script injection
- OS Command injection
- SMTP injection
- SQL injection
- LDAP injection
- XPath injection
- Buffer Overflow
- Canonicalization

#### Data Connectivity Attack

Exploit the data connectivity between application and its database.
Data connection requires a connection string.

- Connetcion String Injection
- Connection String Parameters Pollution (CSPP)
- Connection Pool DoS

# Countermeasures

## Percent Encoding

[Percent Encoding](https://en.wikipedia.org/wiki/Percent-encoding) or URL Encoding is a technique for
secure handling of URL by replaces unsafe and non-ascii characters with % followed by two hexadecimal
digits.

Example:

%20 or + both are used for SPACE

In URL:, there are some reserved character such as '/' that is used to separate paths in 
URL. To use this not as separator, then it must be encoded.

%2F used for '/'

Full list of percent encoded characters 
[here](https://www.degraeve.com/reference/urlencoding.php)

## HTML Encoding

HTML Encoding specify how special character will shown.

#### SQL Injection Contermeasures

- Input validation
- Customized error messages
- Monitoring database traffic
- Limit length of user input

#### XSS Attack Countermeasures

- Testiong tools
- Filtering meta
- Filtering output

#### DOS Attack Countermeasures

- Reverse proxy
- Remove unnecessary functions
- Secure remote administration
- Firewall
- IDS

#### Other Countermeasures

- Dynamic testing
- Source Code analysis
- Strong cryptography
- Use SSL
- Hotfixes / patches
- Cookie timeout
