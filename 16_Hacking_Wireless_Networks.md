**Wireless network** is a computer network that uses wireless data connectionbetween network 
nodes.

# Terms

#### GSM

- Global System for Mobile Communication
- Generations: 2G (GSM), 3G (UMTS), 4G (LTE)
- Frequency: 900 MHz - 1800 MHz

#### Access Point

Access Point (AP) or Wireless Access Point (WAP) is a hardware device that allows wireless 
connectivity to the end devices.

#### Service Set Identifier (SSID)

- 32 bit identification string of the Access Point, the AP's name
- SSID inserted into the header of every data packet

#### Basic Service Set Identifier (BSSID)

- MAC address of the Access Point

#### ISM Band

A frequency band dedicated to the Industrial, Scientific and Medical purpose.

#### Wireless Standards

| Protocol  |  Frequency  | Modulation |
|:---------:|:-----------:|:----------:|
|  802.11a  |    5 GHz    |    OFDM    |
|  802.11b  |   2.4 GHz   |    DSSS    |		
|  802.11g  |   2.4 Ghz   |    OFDM    |
|  802.11n  |  2.4/5 Ghz  | MIMO-OFDM  |
|  802.11ac |    5 Ghz    | MIMO-OFDM  |
| Bluetooth |   2.4 Ghz   |

# Wi-FI 

Wi-Fi is a local area networking technology based on the IEEE 802.11 standard.

## Wi-Fi  Authentication

- Open authentication
- Shared Key authentication

### Open Authentication

|               Client               |    |                     WAP              |
|:----------------------------------:|:--:|:------------------------------------:|
|          Probe Request             | -> |                                      |
|                                    | <- |          Probe Response              |
| Open System Authentication Request | -> |                                      |
|                                    | <- |  Open System Authetication Response  |
|       Association Request          | -> |                                      |
|                                    | <- |      Association Response            | 

- The Probe Request is to discover the network
- The Probe Response contains the parameters (SSID, data rate, encryption, ...)
- The Open System Authentication Request (authentication frame) is to set authentication open, 
the sequence number is set to 0x0001
- The Open System Request Response's sequence number is 0x0002
- The Association Request contains the security parameters (choosen encryption, ...)
- The Association Response complete the assiciation process

### Shared Key Authentication

|               Client               |    |                       WAP                   |
|:----------------------------------:|:--:|:-------------------------------------------:|
|      Authentication Request        | -> |                                             |
|                                    | <- | Authentication Response with Challenge Text |
|   Encypted Challenge Response      | -> |                                             |
|                                    | <- |     Successful / Unseccessful response      |

**Challenge test** :

- The client encrypt the challenge test with his shared key
- The AP decrypt the encrypted challenge test with his shared key, if the decrypted text 
matches, the successful authentication response frame is sent to the client
- This challenge test can be captured by a hacker as a clear text, so the hacker can get the 
shared key

## IEEE 802.1X

IEEE 802.1X is an IEEE Standard for port-based Network Access Control (PNAC). It provides an authentication mechanism to devices 
wishing to attach to a LAN or WLAN.

Extensible Authentication Protocol (EAP) is an authentication framework frequently used in wireless networks and point-to-point 
connections. For example, in IEEE 802.11 (Wi-Fi) the WPA and WPA2 standards have adopted IEEE 
802.1X with one hundred EAP Types as 
the official authentication mechanisms.

#### Parties

- **Supplicant** : a client device (such as a laptop) that wishes to attach to the LAN/WLAN
- **Authenticator** : a network device, such as an Ethernet switch or wireless access point
- **Authentication server** : typically a host running software supporting the RADIUS and EAP protocols

#### Authentication Progress

1. The client may send an EAP-start message.
2. The access point sends an EAP-request identity message.
3. The client's EAP-response packet with the client's identity is "proxied" to the authentication server by the authenticator.
4. The authentication server challenges the client to prove themselves and may send its credentials to prove itself to the client 
(if using mutual authentication).
5. The client checks the server's credentials (if using mutual authentication) and then sends its credentials to the server to 
prove itself.
6. The authentication server accepts or rejects the client's request for connection.
7. If the end user was accepted, the authenticator changes the virtual port with the end user to an authorized state allowing full 
network access to that end user.
8. At log-off, the client virtual port is changed back to the unauthorized state.

## Wardriving

Wardriving is the act of searching for Wi-Fi wireless networks by a person usually in a moving vehicle, using a laptop or 
smartphone.

**Variants** : warwalking, warcycling, warflying (drone)

**Warchalking** is the drawing of [symbols](https://78.media.tumblr.com/tumblr_llnht1usC11qk3ul6o1_500.jpg) in public places to 
advertise Wi-Fi networks.

## Types of Wireless Antennas

#### Directional Antenna

Direction antennas are designed to function in a specific direction to improve efficiency

Some types of directional antenna: [Parabolic antenna](https://en.wikipedia.org/wiki/Parabolic_antenna) , [Yagi-Uda 
antenna](https://en.wikipedia.org/wiki/Yagi_antenna) , [Horn antenna](https://en.wikipedia.org/wiki/Horn_antenna)

#### Omnidirectional antennas

Omnidirectional antenna radiates equal radio power in all directions.
When graphed in three dimensions this radiation pattern is often described as doughnut-shaped.

Use cases: radio broadcating, cell phones, GPS

Some type: [Whip antenna](https://en.wikipedia.org/wiki/Whip_antenna) , [Rubber Ducky 
antenna](https://en.wikipedia.org/wiki/Rubber_Ducky_antenna) , [Monopole antenna](https://en.wikipedia.org/wiki/Monopole_antenna)

## Wireless Encryption

### Wired Equivalent Privacy (WEP)

- Designed to provide the same level of security as that of a wired LAN
- Authentications: Open System authentication, Shared Key (need to provide a key)
- WEP Key is a sequence of hexadecimal values
- WEP Key length: 10 digit (40 or 64 bit), 26 digit (104 or 128), 58 digit (256 bit)
- WEP is used in Physical layer and Data Link layer of OSI model
- Initalization Vector (IV) is 24-bit long
- [WEP work](https://www.quora.com/How-does-WEP-work)

#### Breaking WEP Encryption

1. Monitor the Access Point channel
2. Test injection capability to the AP
3. Use tool for fake authentication
4. Sniff the packets
5. Inject encrypted packets
6. Extract the encryption key form IV with a cracking tool

### Wi-Fi Protected Access (WPA)

- Used for WLAN network based on 802.11i
- Temporal Key Integrity Protocol (TKIP) implements a key mixing function that combines the secret key with the initalization 
vector before passing it to the RC4 cipher. WEP, in comparison, merely concatenated the initialization vector to the root key, and 
passed this value to the RC4 routine.
- TKIP increased the key length to 128-bit
- Implements a sequence counter to protect against replay attacks
- Implements a 64-bit Message Integrity Check, a checksum to protect against tampering
- Initalization Vector is 48-bit long

### WPA2

- Counter Mode Cipher Block Chaining Message Authentication Code Protocol (CCMP) is an enchanced data cryptographic encapsulation 
mechanism designed for data confidentiality
- Implements AES based encryption mode
- Wi-Fi Protected Setup (WPS) allows users to quickly connect to a WPA protected WLAN
- WPA-Personal uses password (Pre-Shared Key(PSK)) for authentication
- WPA-Enterprise includes EAP or RADIUS for centralized authentication

#### Breaking WPA Encryption

1. Brute forcing the PSK with a dictionary attack
2. Capture the Authetication Handshake packets to crack the WPA-PSK offline
3. Deauthenticate client to force to reconnect to brute force the Pairwise Master Key (PMK)

## Wireless Threats

- **Access Contorl Attacks** : evading access controll parameters (MAC spoofing, Rogue Access 
point)
- **Integrity Attacks** : Data frame injection, replay attacks, etc...
- **Confidentiality Attacks** : traffic analysis, session hijacking, MITM, etc...
- **Availability Attacks** : prevent user from accessing the wireless network (flooding, ARP 
poisoning, De-Authentication attacks)
- **Authentication Attacks** : steal identity information or impersonating clients (password 
cracking, identity theft, password guessing)
- **Rogue Access Point** : a fake access point in a place with the legitimate one, with the same 
SSID to monitor victims activity by sniffing packets
- **Client Mis-Association Attacks** : a rogue access point outside the place with the 
legitimate one, when Wi-Fi turned on, it will probe for networks that previously connected to
- **Misconfigured Access Point Attacks** : get legitimate access by taking advantage of access 
point's misconfiguration (default or week password, without password)
- **Unauthorized Association** : a trojan turns the victims computer into an access point to get 
connection with the target network
- **Ad Hoc Connection Attack** : attacker compromise the client ad hoc mode
- **Jamming Signal Attacks** : jamming or blocking the wireless communication, causing a denial 
of service

## Hacking Methodology

#### Wi-Fi Discovery

- Passive footprinting (sniffing packets)
- Active footprinting (probing the AP to get information)

#### GPS Mapping

- Create list of discovered Wi-Fi networks including GPS location

#### Wireless Traffic Analysis

- Capture the packets to reveal any information (SSID, authentication method, ...)

#### Launch Attacks

- ARP poisoning
- MAC spoofing
- De-Authentication
- Rogue access point
- MITM

## Wireless Security Tools

#### Wireless Intrusion Prevention System (WIPS)

- Monitors the wireless network
- Protect against unauthorized access points
- Perform automatic intrusion prevention
- Monitors the radio spectrum to prevents rogue access point and alert the network administrator
- Fingerprint approach to filter devices with spoofed MAC address
- WIPS has three component: server, sensor and console
- Can detect AP misconfiguration
- Detect honeypots
- Mitigate DoS

#### Wi-Fi Security Auditing Tool

- Wireless network auditing
- Troubleshooting
- Intrusion detection / prevention
- Threat mitigation
- Rogue detection
- Zero-day threat protection

## Wi-Fi Countermeasures

- Change default parameters
- Disable remote login to wireless devices
- Wireless IPS deployment
- Use strong password
- Use the latest standards (WPA2 AES)
- MAC filtering
- Update software often
- Enable firewall
- Use network management software

# Bluetooth

- Bluetooth is a wireless technology for exchanging data over short distance
- Range: typically less then 10m
- Operates on the 2.4 GHz
- Discovery feature can control the visibility of the device

#### Bluetooth Attacks

- **BlueSmacking** : flooding echo packages to cause a denial of service
- **BlueBugging** : exploiting bugs in Bluetooth devices to gain remote access
- **BlueJacking** : send unsolicited data to Bluetooth devices
- **BluePrinting** : extract information about the device
- **BlueSnarfing** : steal data from target device

#### Countermeasures

- Check paired devices
- Turn off visibility / turn off Bluetooth if not used
- Use strong PIN
- Use encryption
- Don't accept unknow requests
