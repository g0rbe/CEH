NOTE: THIS MAY CROSS LEGAL BOUNDARIES !!!!!
      YOU MUST HAVE PROPER PERMISSION TO PERFORM THESE ACTIONS

-initates active connection with the target
-direct queries are generated

-enumerated informations:
	-routing information
	-SNMP information
	-DNS information
	-machine name
	-user information
	-group information
	-application and abnners
	-network sharing information
	-network resources

Enumeration using Email ID:
	-extract usefull information (username, domain, ..)

Enumeration using default password:
	-sometimes the default credentials didn't changed

Brute force attack on Active Directory (AD):
	-centralized command and control of doamin users, computers, printers
	-brute force or generating queries to LDAP
	-ports:
		-TCP / UDP 389
	-information from LDAP:
		-username
		-address
		-credentials
		-privileges information

LDAP enumeration:
	-Lightweight Directory Access Protocol
	-accessing and maintaining distributed directory information services
	 in a hierarchical and logicl structure
	-allowing the shareing of information like user, system, network,
	 services, etc. throughout the network
	-provides a central place to store usernames and passwords
	-apps and services connect to LDAP to validate users
	-client initates an LDAP session bt sending an  operation request to
	 Directory System Agent (DSA)
	-communication between client and server uses Basic Encoding Rules
	 (BER)
	-port:
		-TCP 389
	-directory services using LDAP:
		-Active Directory
		-Open Directory
		-Oracle iPlanet
		-OpenLDAP


Enumeration using SNMP:
	-Simple Network Management Protocol
	-allow management of devices (routers, servers, ...)
	-manage network performance
	-find, troubleshoot, solve problems
	-design, plan for network growth
	-application layer protocol
	-ports:
		-UDP 161
		-UDP 162 (Trap)
	-three element:
		-SNMP manager:
			-a sofware running on the management station
			-display collected information
		-SNMP agent:
			-a software running on the network nodes
			-different components are monitored (CPU, RAM, ...)
		-Management Information Base (MIB):
			-a colloection of information organized hierarchically
			 in a virtual database
			-2 types:
				-scaler: single object instance
				-tabular: multiple related object instance
	-use default community strings or guess to extract information
	-community strings:
		-used for authentication
		-types:
			-read-only (read only information from a device)
			-read-write (read information, modify settings)
			-trap
	-SNMP Trap:
		-initated by the SNMP agent
		-report an issue
	-information from SNMP:
		-host
		-devices
		-shares
		-network information
	-versions:
		-v1:
			-no support for encryption and hashing
			-plain text community string
		-v2:
			-no support for encryption and hashing
			-some function added (i.e. get data in bulk from agents)
		-v3:
			-support encryption (DES)
			-support hashing (MD5 or SHA)
			-3 model:
				-NoAuthNoPriv: no encrypt and no hashing
				-AuthNoPriv: no encrypt, just hashing
				-AuthPriv: encryption + hashing used

Enumeration through DNS Zone Transfer:
	-zone transfer is a process to update DNS server, copy containing
	 database record to another DNS server
	-ports:
		-UDP 53 (DNS queries)
		-TCP 53 (DNS Zone Transfer)
	-information from DNS zone transfer process:
		-locating DNS server
		-DNS records
		-hostname
		-IP address
		-username
	-tool:
		-Linux: nslookup, dig

NetBIOS Enumeration:
	-Network Basic Input / Output System
	-allows communication between different application on different
	 system within LAN
	-uses a 16 ASCII Character string to identify devices
	-the initial 15 chars is identifying the device, the last char
	 identify the service
	-session layer protocol
	-ports:
		-UDP 137 (name services)
		-UDP 138 (datagram services)
		-TCP 139 (session services)
	-information from NetBIOS:
		-list of machines within a domain
		-file sharing
		-printer sharing
		-username
		-group information
		-password
		-policies
	-NetBIOS names are classified into the following types:
		-Unique
		-Group
		-Domain name
		-Internet group
		-Multihomed
	-Tools:
		-Windows: nbtstat
		-Linux: nbtscan 

NTP enumeration:
	-Network Time Protocol
	-synchronize the clocks accross the hosts and network devices
	-a lot of services rely on clock settings (logging, login, ...)
	-application layer protocol
	-port:
		-UDP 123
	-based on UTC
	-startum:
		-distance between NTP server and device
		-like TTL
		-start from 1 and increases by every hop
	-attacker may change time to mislead forensic team, who investigate
	 the events (change timestamp)
	-version 3 and above:
		-support a cryptographic authentication technique between
		 NTP peers
		-without authentication, the client do not authenticate the
		 server as a secure source, if the legitimate server goes down,
		 a fake NTP server can replace the real
	-information from NTP:
		-host information
		-client information (IP, machine name, OS)
		-network information
	-tool:
		-Linux: ntpdc, ntptrace, ntpq, nmap, wireshark

SMTP enumeration:
	-Simple Mail Transfer Protocol
	-ensures mail communication between Email servers
	-application layer protocol
	-port:
		-TCP 25 (traditional)
		-TCP 567 
	-enumeration with Telnet
	-commands:
		-HELO (identify domain name of the sender)
		-EXPN (verify Mailbox on localhost)
		-MAIL FROM (identify sender of the email)
		-RCPT TO (specify the message recipients)
		-SIZE (specify maximum supported size)
		-DATA (define data)
		-RSET (reser connection and buffer of SMTP)
		-VRFY (verify the avaliabilty of Mail server)
		-HELP (show help)
		-QUIT (terminate session) 

Enumeration Countermeasures:
	-advanced security softwares
	-updated version of protocols
	-strong security protocols
	-unique and difficult password
	-strong encrypted communications
	-disable unnecessary ports
