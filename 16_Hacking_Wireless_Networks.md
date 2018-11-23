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

