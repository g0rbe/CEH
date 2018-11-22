Web Servers are the programs that are used for hosting services.

Web Servers are deployed on a separate web server hardware or installed on a host as a program.

It delivers content over **Hyper Text Transfer Protocol** (HTTP).

Web Servers support different types of application extensions whereas all of the support **Hypertext Markup Language** (HTML).

#### Web Server Security Issue

Web server vulnerabilities:

- Improper permission of file directories
- Default configurations
- Enabling unnecessary services
- Lack of security
- Bugs
- Misconfigured SSL certificate
- Enabled debugging

#### Open Source Web Servers

- Apache HTTP Server
- Nginx
- Apache Tomcat
- Lighttpd

### Internet Information Services (IIS)

IIS is a Windows-based webserver.

#### Components of IIS

- **Protocol listener** are responsible for receiving and returning protocol-specific requests.
- **HTTP.sys** are responsible for HTTP requests.
- **World Wide Web Pblishing Service** (WWW Service)
- **Windows Process Activation Service** (WAS)

### Web Server Attacks

#### DoS/DDoS

#### DNS Server Hijacking

#### DNS Amplification Attack

Spoof the source address of the DNS request, by the amplification of the size of the request and using 
botnets, it results a DDoS attack.

#### Directory Traversal Attacks

Attacker using trials and error method to access restricted directories to reveal sensitive information.

#### Man-in-the-Middle / Sniffing Attacks

#### Phishing Attacks

#### Website Defacement

After a successful intrusion, attacker alters and modify the content of the website.

#### Webserver Misconfiguration

Attacker looks for misconfigurations and vulnerabilities to exploit.

#### HTTP Response Splitting Attack

[Read more here](http://projects.webappsec.org/w/page/13246931/HTTP%20Response%20Splitting)

#### Web Cache Poisoning Attack

The attacker wipe the actual cache of the webserver and sending crafted request to store fake entries.

#### SSH Brute Force Attack

#### Web Application Attacks

- Cookie Tampering 
- DoS
- SQL Injection
- Session Hijacking
- Cross-Site Request Forgery (CSRF)
- Cross-Site Scripting (XSS)
- Buffer Overflow

# Attack Methodology

## Information Gathering

Collecting information from internet.

### robots.txt

Attacker extract information about internal files.

[Read more](https://en.wikipedia.org/wiki/Robots.txt)

## Web Server Footprinting

Results the server name, type, OS, applications, etc.

Tools:

- Netcraft
- Maltego
- httprecon

## Mirroring a website

Download the website, to inspect offline, without any interaction to the target.

Tool:

- httrack

## Vulnerability Scanning

Automted tool to inspect website and detect vulnerabilities.
These tools perfomr depp inspection of scripts, open ports, banners, etc.

Tools:

- owasp-zap
- openvas

## Hacking Web Passwords

Extract passwords to gain authorized access to the system.
Passwrod may be get from social engineering, tampering the communication, etc.

Password Attacks classification:

- Non-Electronic attacks
- Active online attacks
- Passive online attacks
- Default password
- offline attack

# Countermeasures

- Place web server in a secure zone (behind firewall, IDS, IPS, DMZ)
- Detect potential changes (hashing, script to detect change)
- Auditing ports
- Disable insecure and unnecessary ports
- Using port 443 (HTTPS) over port 80 (HTTP)
- Encrypted traffic
- Server certificate
- Code Access Security Policy
- Disable tracing
- Disable debug complies
- Software update
- Disable default account

#### Patch Management

Hotfix is a small update which fix an issue.
Patch is a bigger of software to fix one or more issues.

Methods:

- Manual download
- Auto-Update

**Patch Management** is an automated process to detect missing security patches, find out solutions, download 
patch, test the patch in an isolated environment then deploy the patch onto the systems.

Tools:

- Microsoft Baseline Security Analyzer (MBSA)
