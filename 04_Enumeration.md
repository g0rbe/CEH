**NOTE**: This may cross legal boundaries, you must have proper permission to perform these actions.

## Basic

- initiates an active connection with the target
- direct queries are generated

- enumerated information:

	- routing information
	- SNMP information
	- DNS information
	- machine name
	- user information
	- group information
	- application and banners
	- network sharing information
	- network resources

## Email

- Extract useful information (username, domain, ..)

## Default password

- sometimes the default credentials are not changed

## Active Directory (AD)

- Centralized command and control of domain users, computers, printers
- Brute force or generating queries to LDAP
- Ports:
	- **TCP / UDP 389**
- Information from LDAP:
	- Username
	- Address
	- Credentials
	- Privileges information

## Lightweight Directory Access Protocol (LDAP)

- Accessing and maintaining distributed directory information services in a hierarchical and logical structure
- Allowing the sharing of information like user, system, network services, etc. throughout the network
- Provides a central place to store usernames and passwords
- Apps and services connect to LDAP to validate users
- Client initiates an LDAP session by sending an operation request to Directory System Agent (DSA)
- Communication between client and server uses Basic Encoding Rules (BER)
- Port:
	- **TCP 389**
- Directory services using LDAP:
	- Active Directory
	- Open Directory
	- Oracle iPlanet
	- OpenLDAP


## Simple Network Management Protocol (SNMP)

- Allow management of devices (routers, servers, ...)
- Manage network performance
- Find, troubleshoot, solve problems
- Design, plan for network growth
- Application layer protocol
- Ports:
	- **UDP 161**
	- **UDP 162** (Trap)
- Three element:
	- SNMP manager:
		- A software running on the management station
		- Display collected information
	- SNMP agent:
		- A software running on the network nodes
		- Different components are monitored (CPU, RAM, ...)
	- Management Information Base (MIB):
		- A collection of information organized hierarchically in a virtual database
		- 2 types:
			- Scaler: single object instance
			- Tabular: multiple related object instance
- Use default community strings or guess to extract information
- Community strings:
	- Used for authentication
	- Types:
		- read-only (read only information from a device)
		- read-write (read information, modify settings)
		- trap
- SNMP Trap:
	- Initiated by the SNMP agent
	- Report an issue
- Information from SNMP:
	- Host
	- Devices
	- Shares
	- Network information
- Versions:
	- v1:
		- No support for encryption and hashing
		- Plain text community string
	- v2:
		- No support for encryption and hashing
		- Some function added (i.e. get data in bulk from agents)
	- v3:
		- Support encryption (DES)
		- Support hashing (MD5 or SHA)
		- 3 model:
			- *NoAuthNoPriv*: no encrypt and no hashing
			- *AuthNoPriv*: no encrypt, just hashing
			- *AuthPriv*: encryption + hashing used

## DNS Zone Transfer
	
- Zone transfer is a process to update DNS server, copy containing database record to another DNS server
- Ports:
	- **UDP 53** (DNS queries)
	- **TCP 53** (DNS Zone Transfer)
- Information from DNS zone transfer process:
	- Locating DNS server
	- DNS records
	- Hostname
	- IP address
	- Username
- Tool:
	- Linux: `nslookup`, `dig`, `host`

[Example](https://security.stackexchange.com/questions/69290/how-to-test-for-zone-transfer):

``` bash
host -t axfr zonetransfer.me nsztm1.digi.ninja.
```

## Network Basic Input/Output System (NetBIOS)

- Allows communication between different application on different system within LAN
- Uses a 16 character long ASCII string to identify devices
- The initial 15 chars is for identifying the device, the last char is for identify the service
- Session layer protocol
- Ports:
	- **UDP 137** (name services)
	- **UDP 138** (datagram services)
	- **TCP 139** (session services)
- Information from NetBIOS:
	- List of machines within a domain
	- File sharing
	- Printer sharing
	- Username
	- Group information
	- Password
	- Policies
- NetBIOS names are classified into the following types:
	- Unique
	- Group
	- Domain name
	- Internet group
	- Multihomed
- Tools:
	- Windows: `nbtstat`
	- Linux: `nbtscan`

## Network Time Protocol (NTP)

- Synchronize the clocks across the hosts and network devices
- A lot of services rely on clock settings (logging, login, ...)
- Application layer protocol
- Port:
	- **UDP 123**
- Based on UTC
- Stratum:
	- Distance between NTP server and device
	- Like TTL
	- Start from 1 and increases by every hop
- Attacker may change time to mislead the forensic team, who investigate the events (change timestamp)
- Version 3 and above:
	- Support a cryptographic authentication technique between NTP peers
	- Without authentication, the client does not authenticate with the server as a secure source, if the legitimate server goes down, a fake NTP server can replace the real
- Information from NTP:
	- Host information
	- Client information (IP, machine name, OS)
	- Network information
- Tool:
	- Windows: `NetTime`
	- Linux: `ntpdc`, `ntptrace`, `ntpq`, `nmap`, `wireshark`

## Simple Mail Transfer Protocol (SMTP)

- Ensures mail communication between Email servers
- Application layer protocol
- Port:
	- **TCP 25** (Unencrypted)
	- **TCP 587** (TLS)
- Enumeration with Telnet
- Commands:
	- `HELO`: identify domain name of the sender
	- `EXPN`: verify Mailbox on localhost
	- `MAIL FROM`: identify sender of the email
	- `RCPT TO` specify the message recipients
	- `SIZE`: specify maximum supported size
	- `DATA`: define data
	- `RSET`: reset connection and buffer of SMTP
	- `VRFY`: verify the availability of Mail server
	- `HELP`: show help
	- `QUIT`: terminate session

## Countermeasures

- Advanced security software
- Updated version of protocols
- Strong security protocols
- Unique and difficult password
- Strong encrypted communications
- Disable unnecessary ports
