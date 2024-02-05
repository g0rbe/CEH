## Methodology

- Cracking Password
- Escalating Privileges
- Executing Applications
- Hiding Files
- Covering Tracks

## Goals

- Bypass the access control
- Gain access to the system
- Exploit vulnerabilities
- Gain privileges
- Execute applications
- Hide malicious activities
- Hide the evidence of compromising

## Password Cracking

Three type of authentication factors:

- **Something i have** : username, password, ...
- **Something i am** : biometrics, ...
- **Something i possess** : allowed / registered devices, ...

Password Cracking is the method for extracting the password to gain authorized access to the target system in the guise of a legitimate user. 
Usually, only the username and password authentication are configured, but now password authentication is moving toward two-factor authentication or multiple-factor authentication. 

A good password contains:

- Case sensitive letters
- Special characters
- Numbers
- Lengthy password (more than 8 characters)

### Types of Password Attacks

#### Non-Electronic Attacks

Don't require any type of technical understanding and knowledge.

Example:

- Shoulder surfing
- Social Engineering
- Dumpster Diving

#### Active Online Attack

Directly interact with the target for cracking the password.

##### Dictionary Attack

A password-cracking application is used along with a dictionary file. 
This dictionary file contains an entire dictionary or a list of known and common words. 
This is the most common type of password cracking. 
Systems are not vulnerable if they use a strong, unique alphanumeric password. 

##### Brute Force Attack

Attempt to recover the password by trying every possible combination of characters until the password is accepted.
Common and basic technique.

##### Hash Injection

Compromising a workstation by exploiting the vulnerability, and extract the log-on hashes. 
Hashing and other cryptography knowledge require.


#### Passive Online Attacks

Password Attack without probing the target.

##### Wire Sniffing

Sniffing the packets with a packet sniffing tool within the Local Area Network (LAN), and inspecting the captured packets.

##### Man-in-the-Middle (MITM) Attack

The attacker involves himself in the communication, inserts himself in.

MITM Attacks:

- SSL Strip
- Burp Suite
- Browser Exploitation Framework (BeEF)

**Replay Attack** : Capture the packets and extract information such as passwords from it. Then generating replay traffic with the injection of extracted information to gain access to the system.

#### Default Password 

Gain access to the system by using the preconfigured password. The default password can be found on the manufacturer site or through online tools.

#### Offline Attack

##### Pre-computed hashes and Rainbow table

Comparing a password using a rainbow table. 
Rainbow Table is the pre-generated hashes of the words in a dictionary or the combination of characters. 
The advantage of Rainbow Table is the speed because it takes less time to compare the hashes. 
The disadvantage is the time and storage, it takes much more time and storage to compute and store the hashes. 

##### Distributed Network Attack (DNA)

Using the unused processing power of machines across the network to decrypt the hashes.
DNA requires a DNA manager and DNS Clients. DNA Manager allocates small tasks over the distributed network to be computed in the background.

#### Password Guessing

The attacker uses the information extracted by initial phases and guess the password.
Not a common method and the rate of success is low.

### USB Drive

Attacker plug in a USB Drive that contains a password hacking tool.
Windows Autorun feature allows running the application automatically, if enabled.

### Microsoft Authentication

*Authentication* is a verification process to identify any user or device.

Microsoft authentication protocols:

- Kerberos
- Security Account Manager (SAM)
- NT LAN Manager (NTLM)
- LM

#### Security Account Manager (SAM)

SAM is a database that stores credentials and other account parameters such as passwords for the authentication process in Windows.
While the OS running, this database is locked to be accessed by any other service and process.
There are several other security algorithms that are applied to the database to secure and validate the integrity of data.
Within Microsoft, SAM stores password in LM/NTLM hashing format.
Windows XP and later versions do not store the value of LM hash, or when LM hash is exceeding 14 characters, it stores blank or dummy value instead.

**Format** :

```
Username: user ID: LM hash: NTLM hash:::
```

**Location**: 

```
C:\windows\system32\config\SAM
```

#### NTLM Authentication

NT Lan Manager is a proprietary authentication protocol by Microsoft.
In the authentication process, the user sends login credentials to a domain controller in a hashed format.
Domain controller responds to a challenge known as **nonce** to be encrypted by the password's hash.
This challenge is a 16-byte random number generated by the domain controller.
By comparing the challenge with the database, the domain controller permits or deny the login.
Microsoft upgraded its default authentication mechanism from NTLM to Kerberos.

NTLM has two versions:

- NTLMv1 (Older)
- NTLMv2 (Improved)

For an additional security layer, NTLM is combined with Security Support Provider.

#### Kerberos

Kerberos is an advanced authentication protocol.
Clients receive tickets from Kerberos Key Distributor Center (KDC)

KDC depends upon two components:

- Authentication Server (AS)
- Ticket-Granting Server (TGS)

The client sends a request to the AS to grant Tick-granting-ticket.
The AS authenticates the client by comparing the user identity and password from its database and reply with Tick-Granting Ticket and a session key.
The session key is for a session between the client and the TGS.
Now, the client can communicate with the Ticket-Granting Server (TGS).
The client sends the TGT to TGS, asking for communication with another user.
TGS reply with a Ticket and session key.
Ticket and Session key is for communicating with other users within a trusted domain.

### Password salting

Password salting is the process of adding additional character to the password by a one-way function.
This makes the password more difficult to reverse the hash.
The function of salting is to defeat the Dictionary Attacks and Rainbow Table attacks.

### Password file by Operating Systems

- Windows: SAM (`C:\windows\system32\config\SAM`)
- Linux: Shadow (`/etc/shadow`)
- Domain Controller: NTDS:DIT

### Password Cracking tools

- pwdump7
- fgdump
- RainbowCrack
- Cain and Abel
- John The Ripper
- Pyrit
- Hashcat

### Password Cracking Countermeasures

- Change default passwords
- Do not store/save passwords in applications
- Do not use guessable passwords
- Set a strong password
- Password encryption
- Keep credentials secure and secret
- Enable SYSKEY
- Password salting
- Advance security audits
- Periodically update passwords
- Monitor attacks
- Different password for each service
- Configure policies for incorrect password attempts

## Escalating Privileges

The main goal is to get high-level access to the system.

### Horizontal Privileges Escalation

The attacker attempts to gain access to a user that has the same set of privileges. 

### Vertical Privileges Escalation

The attacker attempts to escalate privileges to a higher level.
Vertical privileges occur when an attacker is trying to gain access to the Administrator account.
Higher privileges allow an attacker to access sensitive information, modify files, and execute programs.

### Privilege Escalation using DLL Hijacking

Applications need Dynamic Link Libraries (DLL) to run.
In Windows, most of the application search for DLL in directories, instead of using the full, qualified path.
The Attacker replaces the DLL with a malicious one.

DLL Hijacking tool: Metasploit

**Known DLL**s are specified in the registry key:

```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\
```

*Search paths* used by Microsoft:

- Directory of application or current directory
- System directory (i.e. C:\\Windows\\System32\)
- Windows directory

## Executing Applications

The Attacker's next step is to execute malicious applications.
This execution is for gaining access to system resources, crack passwords, set up backdoors, and many more.
This process is called "System Owning".

Goals:

- Install malware to collect information
- Setup Backdoor to maintain access
- crack passwords and scripts
- Install Keylogger
- etc...

### RemoteExec

RemoteExec is software designed for the installation of an application, execution of code and scripts remotely.
RemoteExec can upload files across the network.

Features:

- Deploy packages
- Remotely execution of programs
- Scheduling execution
- Remote configuration (settings, files, ...)
- Remote controlling (turn off, lock, ...)

### PDQ Deploy

PDQ Deploy is a software for system administrators to install and send updates silently to the remote systems.
It can silently deploy almost every application (.exe, .msi, ...).
It can install, uninstall, copy, execute, and send files.

### Keyloggers

Keystroke logging, keylogging, and keyboard capturing is a process of monitoring and/or recording the actions of any user.
Logging the actions to steal information from the target machine.

Goals:

- Capture the pushed buttons
- Take screenshots
- Capture mouse
- Many more...

#### Software Keyloggers

Software-based keyloggers are remotely installed, or send it to the target to execute the application.

Types:

- Application keyloggers
- Kernel keyloggers
- Hypervisor-based keyloggers
- Form Grabbing based keyloggers

#### Hardware Keyloggers

It is a physical hardware device that is installed by physically accessing the device.

Types:

- PC/BIOS Embedded keyloggers
- Keylogger keyboard
- External keylogger (video, bluetooth, wi-fi, acoustic, ...)

#### Anti-Keyloggers

Anti-Keylogger is an application that ensures protection against keylogging by providing SSL protection, keylogging protection, clipboard logging protection, and screen logging protection.

Anti-Keylogger softwares:

- Zemana
- Spyshelter Anti-keylogger
- Anti-Keylogger

 
#### Key-logging Countermeasures

- Keystroke interference software
- Don't click on doubtful URLs
- Anti-Keylogger software
- On-Screen keyboard for secrets
- Physical monitoring
- Host-based IDS
- File scanning prior to installation

### Spyware

Spywares are the software designed for gathering user interaction information with a system such as login credentials, emails, and many more without informing the user of the system.
The gathered information is sent to a remote destination.
Spyware hides its files and processes to avoid detection.

Types:

- Adware
- System monitors
- Tracking cookies
- Trojans

Features:

- Tracking users (i.e. keylogging)
- Monitor user's activity
- Blocking services
- Remote delivery of logs
- Email tracking
- Record removable media communication (i.e. USB)
- Voice recording
- Video recording
- Tracking location (GPS)
- Mobile tracking

### Rootkits

A rootkit is software designed to provide privileged access to a remote user over a system, creates a backdoor.
Deployed after attackers gain high-level access to a system.
Rootkits often mask their existence to avoid detection.

#### Types

- **Application-level rootkit**: perform manipulation of standard application file with an injection of codes.
- **Kernel-level rootkit**: inject malicious code to the kernel
- **Hardware/Firmware level rootkit**: built into a chipset
- **Hypervisor level rootkit**: exploits hardware features like AMD-V or Intel VT
- **Boot Loader level rootkits (Bootkits)**: replace the legitimate boot loader with the malicious one which enables the bootkit to activated before an OS run. It can attack Master Boot Record (MBR), Volume Boot Record (VBR), or boot sector.
It can be used to attack full disk encryption systems, hack encryption keys and passwords.

#### Tool

- Avatar
- Necurs
- Azazel
- ZeroAccess

#### Detecting and Defending Rootkits

- Integrity-Based Detection
- Digital signatures
- Difference-based detection
- Behavior-based detection
- Cross-view based detection
- Run-time execution path profiling
- Anti-rootkit software
- Deploying a network-based firewall
- Host-based firewall
- Install application/OS from trusted sources
- Integrity verification
- Kernel memory dump analysis

Unix tools: 

- Zeppo
- chrootkit

Windows tools:

- Microsoft Sysinternals Rootkit Revealer
- Sophos Anti-Rootkit

### New Technology File System (NTFS) Data Stream

NTFS is a Windows file system by Microsoft.
NTFS is the default file system for Windows 10,- 7,- Vista,- XP,- 2000,- NT.

#### Alternate Data Stream (ADS)

ADS is a file attribute in the NTFS file system, contains metadata for locating a particular file.
ADS is capable of hiding file data into an existing file without altering or modifying any noticeable changes.
It can be a security threat because it can hide malicious files.

NTFS Streams Countermeasures:

- Moving file to a FAT partition (FAT doesn't support ADS, but this will corrupt the file)
- Third-party tools (ADS Spy, ADS Tools, LADS, ...)

### Steganography

Steganography is a technique for hiding sensitive information in an ordinary message to ensure confidentiality.
Steganography uses encryption to maintain confidentiality and integrity.
It hides the encrypted data to avoid detection.
An attacker may use this technique to transfer data without being detected.

#### Classification of Steganography

- **Technical Steganography** includes concealing information using methods like using the invisible link, microdots.
- **Linguistic Steganography** uses text as covering media to hide the information using ciphers and code to hide information.

#### Types of Steganography

- Whitespace Steganography
- Image/Pixel Steganography
- Document Steganography
- Video Steganography
- Audio Steganography
- File/Folder Steganography
- Spam/Email Steganography
- Web Steganography
- Frequency Steganography
- Least Significant Bit Steganography

##### Whitespace Steganography

Hide information in a text file using extra blank space inserted in between words covering the file.
Using LZW and Huffman compression method to decrease the size of the message.

##### Image Steganography

Hidden information can be kept in image formats, such as PNG, JPG, others.
Image steganography places redundant bits of the image in the message.
It cannot be detected by the human eye.

Techniques:

- Least significant bit insertion
- Masking and filtering
- Algorithm and transformations

Tools:

- OpenStego
- QuickStego
- Steghide (Linux)

#### Steganalysis

Analysis of suspected information using steganography techniques to discover and retrieve the hidden information.

Methods:

- Stego-only: have only stego object
- Known stego: have stego object, algorithm, and cover
- Known message: have stego object and hidden message
- Known cover: have stego object and cover
- Chosen message: generate stego form known message to identify the algorithm
- Chosen stego: have stego object and algorithm


## Covering tracks

After gaining access, escalating privileges, executing applications, the next step is to wipe the evidence.
In this phase, the attacker removes all the event logs, error messages, and other evidence to prevent its attack from being discovered easily.

Common techniques:

- Disable auditing
- Clearing logs
- Manipulating logs

### Disable auditing

Preventing another security mechanism to indicate an alert of any sort of intrusion, and leaving no trace on the machine.
The best practice for leaving no track and prevent detection is by disabling the auditing as you logged in on the system.
It will not only prevent to log events, but also resist the detection.
Auditing in a system is enabled to detect and track events.

List auditing categories in windows:

```
C:\Windows\system32>auditpol /list /category /v
```

Check all category audit policies:

```
C:\Windows\system32>auditpol /get /category:*
```

### Clearing logs

By clearing logs, all events logged during the compromise will be erased.

Folder of log files:

Windows 2000/Server2003/Windows XP:

```
%SystemRoot%\System32\Config
```

Server 2008/Vista and up:

```
%SystemRoot%\system32\winevt\logs
```

Linux, OpenBSD:

```
/var/log/
```

### Other methods

- Clear cookies
- Clear cache
- Clear temporary files
- CCleaner
- Clear Most Recent Used (MRU)
