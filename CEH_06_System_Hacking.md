### System Hacking Methodology

- Cracking Password
- Escalating Privileges
- Executing Applications
- Hiding Files
- Covering Tracks

### Goals

- Bypass the access control
- Gain access to the system
- Exploit vulnerabilities
- Gain privileges
- Execute applications
- Hide malicious activities
- Hide the evidence of compromising

# Password Cracking

Three type of authentication factors:

- **Something i have** : username, password, ...
- **Something i am** : biometrics, ...
- **Something i possess** : allowed / registered devices, ...

Password Cracking is the method for extracting the password to gain authorized access to the target system in the guise of a legitimate user. 
Usually, only the username and password authentication are configured, but now password authentication is moving toward two-factor authentication or multiple-factor authentication. 

A good password contain:

- Case sensitive letters
- Special characters
- Numbers
- Lengthy password (more than 8 character)

## Types of Password Attacks

### Non-Electronic Attacks

Dont require any type of technical understanding and knowledge.

Example:

- Shoulder surfing
- Social Engineering
- Dumpster Diving

### Active Online Attack

Directly interact with the target for cracking password.

#### Dictionary Attack

A password cracking application is used along with with a dictionary file. 
This dictionary file contains entire dictionary or a list of known and common words. 
This is the most common type of password cracking. 
Systems are not vulnerable if they use a strong, unique alphanumeric password. 

#### Brute Force Attack

Attempt to recover the password by trying every possible combination of characters until password is accepted.
Common and basic technique.

#### Hash Injection

Compromising a workstation by exploiting the vulnerability, and extarct the log-on hashes. 
Hashing and other cryptography knowledge require.


### Passive Online Attacks

Password Attack without probing the target.

#### Wire Sniffing

Sniffing the packets with a packet sniffing tool within the Local Area Network (LAN), and inspecting the captured packets.

#### Man-in-the-Middle (MITM) Attack

The attacket involves himself into the communication, insert himself in.

MITM Attacks:

- SSL Strip
- Burp Suite
- Browser Exploitation Framwork (BeEF)

**Replay Attack** : Capture the packets and extract information such as password from it. Then generating a replay traffic with the injection of extracted information to gain access to the system.

### Default Password 

Gain access to the system by using the preconfigured password. The default password can be find on the manufacturer site or through online tools.

### Offline Attack

#### Pre-computed hashes and Rainbow table

Comparing a password using a rainbow table. 
Rainbow Table is the pregenrated hashes of the words in a dictionary or the combination of characters. 
The advantage of Rainbow Table is the speed, because it takes less time to compare the hashes. 
The disadvantage is the time and storage, it takes much more time and storage to compute and store the hashes. 

#### Distributed Network Attack (DNA)

Using the unused processing power of machines across the network to decrypt the hashes.
DNA requires a DNA manager and DNS Clients. DNA Manager allocate small tasks over the distributed network to be computed in the backgroud.

### Password Guessing

The attacker uses the information extracted by initial phases and guess the password.
Not common method and the rate of failure is high.

### USB Drive

Attacker plug in an USB Drive that contain a password hacking tool.
Windows Autorun feature allows running the application automatically, if enabled.

## Microsoft Authentication

**Authentication** is a verification process to identify any user or device.

Microsoft authentication protocols:

- Kerberos
- Security Account Manager (SAM)
- NT LAN Manager (NTLM)
- LM

### Security Account Manager (SAM)

SAM is database that stores credentials and other account parameters such as passwords for the authentication process in Windows.
While the OS running, this database os locked to be accessed by any other service and process.
There are several other security algorithms are applied to the database to secure and validate the intergrity of data.
Within Microsoft, SAM stores password in LM/NTLM hashing format.
Windows XP and later versions do not store the value of LM hash, or when LM hash is exceeding 14 characters, it stores blank or dummy value instead.

**Format** :

``` sh
Username: user ID: LM hash: NTLM hash:::
```

**Location**: 

``` sh
C:\windows\system32\config\SAM
```

### NTLM Authentication

NT Lan Manager is a proprietary authentication protocol by Microsoft.
In the authentication process, user sends login credentials to a domain controller in hashed format.
Domain controller responds to a challenge known as **nonce** to be encrypted by the password's hash.
This challenge is a 16 byte random number generated ny the domain controller.
By comparing the challenge with the database, domain controller permit or deny the login.
Microsoft upgraded its default authentication mechanism from NTLM to Kerberos.

NTLM has two version:

- NTLMv1 (Older)
- NTLMv2 (Improved)

For additional security layer, NTLM is combined with Security Support Provider.

### Kerberos

Kerberos is an advanced authentication protocol.
Clients receive tickets from Kerberos Key Distributor Center (KDC)

KDC depend upon two components:

- Authentication Server (AS)
- Ticket-Granting Server (TGS)

The client send a request to the AS to grant Tick-granting-ticket.
The AS authenticates the client by comparing the user identity and password from its datbase and reply with Tick-Granting Ticket and a session key.
The session key is for a session between client and TGS.
Now, client can communicate with the Ticket-Granting Server (TGS).
The client send TGT to TGS, ask for communication with another user.
TGS reply with a Ticket and session key.
Ticket and Session key is for communicating with other user within a trusted domain.

### Password salting

Password salting is the process of adding additional character in the password to one-way function.
This makes the password more difficult to reverse the hash.
The function os salting is to defeat the Dictionary Attacks and Rainbow Table attacks

### Password file by Operating Systems

Windows: SAM
Linux: SHADOW
Domain Controller: NTDS:DIT

#### Password Cracking tools

- pwdump7
- fgdump
- RainbowCrack
- Cain and Abel
- John The Ripper
- Pyrit
- Hashcat

## Escalating Privileges

The main goal is to get a high-level access to the system.

### Horizontal Privileges Escalation

The attacker attempts to gain access to user that has same set of privileges. 

### Vertical Privileges Escalation

The attacker attepmts to escalate privileges to a higher level.
Vertical privileges occurs when attacker is trying to gain access to the Administrator account.
Higher privileges allow attacker to access sensitive information, modify files and execute programs.

#### Privilege Escalation using DLL Hijacking

Applications need Dynamic Link Libraries (DLL) to run.
In Windows, most of the application search for DLL in directories, instead of using the full qualified path.
The Attacker replace the DLL to a malicious one.

DLL Hijacking tool: Metasploit

**Known DLL**s are specified in the registry key:

``` sh
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\
```

**Search paths** used by Microsoft:

- Directory of application or current directory
- System directory (i.e. C:\\Windows\\System32\)
- Windows directory

## Executing Applications

The Attacker's next step is to execute malicious applications.
This execution is for gaining access to system resources, crack passwords, set up backdoors and many more.
This process is called as "System Owning".

Goals:

- Install malware to collect information
- Setup Backdoor to maintain access
- crack passwords and scripts
- Install Keylogger
- etc...

### RemoteExec

RemoteExec is software designed for installation of application, execution of code and scripts remotely.
RemoteExec can upload file across the network.

Features:

- Deploy packages
- Remotely execution of programs
- Scheduling execution
- Remote configuration (settings, files, ...)
- Remote controlling (turn off, lock, ...)

### PDQ Deploy

PDQ Deploy is a software for system administrators to install and send updates silently to the remote systems.
It can silently deploy almost every application (.exe, .msi, ...).
It can install, uninstall, copy, execute and send files.

