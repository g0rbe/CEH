# Mobile Platform Attack Vectors

### OWASP Top 10 Mobile Threats

[OWASP Mobile Security Project](https://www.owasp.org/index.php/OWASP_Mobile_Security_Project#Top_Ten_Mobile_Risks) maintain a list 
of the most common mobile security risks.

#### Top Ten (2014)

- **1.** Weak Server Side Controls
- **2.** Insecure Data Storage
- **3.** Insufficient Transport Layer Protection
- **4.** Unintended Data Leakage
- **5.** Poor Authorization and Authentication
- **6.** Broken Cryptography
- **7.** Client Side Injection
- **8.** Security Decisions via Untrusted Inputs
- **9.** Impoper Session Handling
- **10.** Lack of Binary Protections

#### Top Ten (2016)

- **1.** Improper Platform Usage: misuse of a platform feature or failure to use a platform security controls
- **2.** Insecure Data Storage: insecure data storage + unintended data leakage
- **3.** Insecure Communication: poor handshaking, incorrect SSL, weak negotiation, cleartext communication of sensitive assests, 
...
- **4.** Insecure Authentication: captures notions of authenticating the end user or bad session management
- **5.** Insuficient Cryptography: cryptography was attempted, but it wasn't done correctly
- **6.** Insecure Authorization: capture any failures in authorization
- **7.** Client Code Quality: all of the code-level implementation problem in the mobile client
- **8.** Code Tampering: binary patching, local resource modification, method hooking, dynamic memory modification, ...
- **9.** Reverse Engineering: analysis of the final core binary to determina the source code, libarires, ...
- **10.** Extraneous Finctionality: internal devlopement security controls that are not intended to be released into a production 
environment

### Attack Vector

#### Basic Threats

- Malware / rootkit
- Data Loss
- Data Tampering
- Data Exfiltration

#### Vulnerabilites And Risks on Mobile Platforms

- Malicious third-party application / in the store
- Application vulnerability
- Data security
- Excessive permissions
- Weak encryptions
- Operating System update issue
- Application update issue
- Jailbreaking / rooting
- Physical attack

#### OS Sandboxing Issue

- Sandbox is a security mechanism for separating running programs, usually in an effort to mitigate system failures or software 
vulnerabilities from spreading
- Sandbox limits the app's access to files, preferences, network resources, ...
- Advanced malware designed to bypass it, by fragment code or put sleep timer in the script to bypass the inspection process

# Android

#### Device Administration API

- Provides device administration features at the system level
- This API allows to create security-aware apps that are useful in the enterprise settings, where require rich control over employee 
devices

#### Rooting

- A process of allowing user to attain privileged control
- Needed for modify settings, get full control over the kernel or install custom ROMs
