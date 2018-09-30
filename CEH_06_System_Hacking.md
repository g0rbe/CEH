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
