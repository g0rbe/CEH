The Internet of things (IoT) is the network of devices, vehicles, and home appliances that contain electronics, software, actuators, 
and connectivity which allows these things to connect, interact and exchange data.
IoT involves extending Internet connectivity beyond standard devices, such as desktops, laptops, smartphones and tablets, to any 
range of traditionally dumb or non-internet-enabled physical devices and everyday objects. Embedded with technology, these devices 
can communicate and interact over the Internet, and they can be remotely monitored and controlled.

#### Main Components

1. Sensors
2. Device
3. Gateway
4. Cloud

#### IoT Architecture

1. **Perception Layer** : sensors that gather information about the environment (heat sensor)
2. **Transport Layer** : transfer the sensor data through network (Wi-Fi, Bluetooth, ...)
3. **Processing Layer** : stores, processes, analyses data (cloud computing, big data, ...)
4. **Application Layer** : delivering application specific services to the user
5. **Business Layer** : manage the whole IoT system (business and profit modell, user's privacy)

## IoT Technologies

- IoT uses IPv6 due to the limited number of IPv4 addresses

#### Shart-Range Wireless Communication

- Bluetooth Low Energy (BLE)
- Wi-FI
- Radio-Frequency Identification (RFID)
- Light-Fidelity (Li-Fi): similar to Wi-Fi, but using visible ligth for communication
- Near-Field Communication (NFC)

#### Medium-Range Wireless Communication

- LTE-Advanced : formally submitted as a candidate 4G, often being described as 3.9G (beyond 3G but pre-4G)
- Wi-Fi HaLow : uses 900MHz to provide extended range, lower energy comsumption

#### Long Range Wireless Communication

- Low-Power Wild-Area Network (LPWAN) : designed to allow long range communication at a low bit rate among things
- Very Small Aperture Terminal (VSAT) : satellite communication technologu uses small dish antennas
- Cellular

#### Wired Communication

- Ethernet
- Power-Line Communication (PLC) : using electrical wiring to carry power and data

#### Operating System

- Linux on embedded systems
- Windows IoT

## IoT Communication Models

#### Device-To-Device Model

- The devices communicating with each other without interfering any other device
- Using communication medium such as a wireless network

#### Device-To-Cloud Model

- The IoT device directly communicating with the application server
- The application server provide information exchange between these devices

#### Device-To-Gateway Model

- Gateway collects the data from the sensors, then send it to the application server
- Gateway provides security or information and protocol translation

#### Back-End Data-Sharing Model

- Used a collective partnership between different application providers
- Access granted to the uploaded data to third-parties
- An extended Device-To-Cloud model

## Challenges to IoT


- Lack of security
- Vulnerable interfaces
- Physical security risk
- Lack of vendor support
- Difficult ot update firmware and OS
- Interoperability issues

#### OWASP Top Ten IoT (2014)

1. Insecure web interface
2. Insufficient authentication / authorization
3. Insecure network services
4. Lack of transport encryption / integrity verification
5. Privacy concerns
6. Insecure cloud interface
7. Insecure mobile interface
8. Insufficient security configurability
9. Insecure software / hardware
10. Poor physical security

### Common Attacks

- Device memory containing credentials
- Access control
- Firmware extraction
- Privilege escalation
- Reseting to an insecure state
- Removal of storage media
- Web attacks
- Firmware attack
- Network service attacks
- Unencrypted local data storage
- Confidentiality and integrity issues
- Cloud computing attacks
- Malicious updates
- Insecure APIs
- Mobile application threats
- DoS / DDoS
- Rolling Code Attack: attacker capture signal from transmitter device, simultaneously blocking the receiver to receive 
the signal, later it will used to gain unauthorized access (steal car with captured signal)
- BlueBorn Attack: using different exploits to gain unauthorized access to the target device
- Jamming Attack: jamming the signal to prevent the communication of devices
- Backdoor (not just IoT related)
- Eavesdropping
- Sybil attack
- Exploit kits
- Man-in-the-middle attack
- Replay attack
- Forged malicious devices
- Side channel attack
- Ransomware attack

## Hacking Methodology

#### Information Gathering

- IP address
- Running protocols
- Open ports
- Type of device
- Vendor
- [shodan](https://www.shodan.io/) is a helpful search engine for IoT

#### Vulnerability Scanning

- Scanning the network and devices to find vulnerabilities
- Search for weak password
- Software and firmware vulnerabilities
- Tools: nmap, hping, ...

#### Attack

- Exploiting vulnerabilities
- Tools: HackRF

#### Gain Access

- Gain unauthorized access 
- Privilege escalation
- Install backdoor

#### Maintain Attack

- Logging out
- Clearing logs
- Covering tracks

## Countermeasures

- Firmware update
- Block unnecessary ports
- Disable telnet
- Use encrypted communication (SSL/TLS)
- Use strong password
- Encrypt drives
- Periodic assessment of devices
- Secure password recovery
- Two-Factor Authentication
- Disable UPnP
