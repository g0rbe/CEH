With sniffing, you can monitor all sorts of traffic either protected or unprotected.
Sniffing is the process pf scanning and monitoring of the captured data like DNS traffic, web traffic and many more by enabling the promiscuous mode on the network interface.
The attacker can reveal information from it such as usernames and passwords.
Anyone within the same LAN can sniff the packets.

#### Working of Sniffers

In the process of sniffing, the attacker gets connected to the target network to start sniffing.
Sniffers turns Network Interface Card (NIC) into promiscuous mode.
Promiscuous mode is a mode of the interface in which NIC respond for every packet it receives.
The attacker decrypt the packets to extract information.

Concept:

- Switch maintain its MAC table to validate the connceted hosts
- Attacker alter this table with Port Mirroring, Switched Port Analyzer (SPAN) and many other techniques
- All packets copied to the attacker

**Switch** forward broadcast and multicat to all ports, but forward unicast packets to a specific port.
**Hub** transmits all packets to all ports.

### Types of Sniffing

#### Passive Sniffing

There is no need of sending additional packet or interfering the device, for example when connected to a hub.

#### Active Sniffing

Attacker has to send additional packets to the connected device to start receiving packets.

Techniques:

- MAC Flooding
- DHCP Attacks
- DNS Poisoning
- Switch Port Stealing
- ARP Poisoning
- Spoofing

#### Hardware Protocol Analyzer

A hardware or software that analyze the captured packets and signals over the transmission channel.
Hardware Protocol Analyzers are the physical equipment which is used to capture without interfering the network traffic.
A major advantage of this hardwares are the mobility, flexibility and throughput.

Hardware Protocol Analyzer can:

- Monitor network usage
- Identify traffic
- Decrypt packets
- Extract information
- Seize packet

### Switch Port Analyzer (SPAN) Port

In other name: **Port Mirroring**

It is used on a network switch to send a copy of network packets seen on one switch port (or an entire VLAN) to a network monitorin connectionon an other switch port.

### Wiretapping

Gaining information by tapping the signal from wire such as telephone lines or the internet.
Wiretapping mostly performed by a third party.
Legal Wiretapping is called **legal interception** which is mostly performed by governmentse or security agencies.

#### Active Wiretapping 

Monitoring and recording the information with alteration of the communication.

#### Passive Wiretapping

Monitoring and recording the information without any alteration in the communication.

#### Lawful Interception

Wiretapping with legal authorization which allows law enforcement agencies to wiretap the communication of user.



(**!!!**)

Telecommunication standardization organization standardized the legal interception gateways for the interception of communication by agencies.

#### Planning tool for Resource Integration, Synchronization, and Management (PRISM)

PRISM is a tool designed to collect information and process that passing through American servers.
Developed by Special Source Operation (SSO) division of National Security Agencies (NSA).
PRISM is intended for identificating and monitoring of suspicious communication.
Internet traffic routing through the US, or data stored on a US server are wiretap by NSA.

## Sniffing Countermeasures

- HTTPS instead of HTTP
- SFTP instead of FTP
- Switch instead of Hub
- Port security
- DHCP Snooping
- Dynamic ARP inspection
- Source guard
- Sniffing detection tool
- Strong encryption protocol

#### Detection:

- Ping method
- ARP method
- Promiscuous port detection

# MAC Attacks

**Media Access Control** (MAC) is the physical address of a device.
MAC ddress is a 48-bit unique identfication number that is assiged to a network device for communication at data-link layer (layer 2).
First 24 bits are the Object Unique Identifier (QUI), the last 24 bits are the Network Interface Controller (NIC).

#### MAC Address Table / CAM Table

MAC address table or Content-Addressable Memory table is used in ethernet switches to record MAC address, and it's associated information which is used to  forward packets.


The switch observe the incoming frames and records the source MAC of the frames in it's MAC address table. It also records the specific port for the source MAC address.
Based on this, switch can make intelligent frame forwarding.
Switch removes MAC from the table after switch not seen it for a while.
