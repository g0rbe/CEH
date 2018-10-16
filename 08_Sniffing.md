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

#### MAC Flooding

Attacker sends random MAC addresses mapped with random IP to overflow the storage cappacity of CAM table.
CAM table has a fixed length, so when filled, switch act as a hub, broadcast every packet on every port, help attacker to sniff packets.

Linux tool:

- macof

#### Switch Port Stealing

This technique base on MAC flooding, the attacker send bogus ARP packets with the source MAC address of the target and destination address of its own.
The switch update the CAM table because of it.

If the attacker send a bogus ARP packet immediatelly after the target packet, the attacker will get the respond instead of the target.

#### Defending against MAC Attacks

Port Security is used to bind MAC addres of known devices to the physical ports and violation action is also defined.


# DHCP Attacks

## Dynamic Host Configuration Protocol (DHCP)

DHCP is the process of allocating the IP address dynamically so these addresses are assigned automatically and they can be reused when hosts dont need them.
**Round Trip Time** is the measurement of time from discovery of DHCP server until obtaining the leased IP address.

**IPv4 DHCP process**:

By using UDP broadcast, DHCP client sends an initial **DHCP-Discovery** packet.
The DHCP server reply with a **DHCP-Offer** packet, offering the configuration parameters.
The DHCP client send back a **DHCP-Request** packet destined for DHCP server for requesting the DHCP parameters.
Finally, the DHCP server send the **DHCP-Acknowledgement** packet containing configuration parameters.

CLIENT				SERVER 
--------------------------------------
DHCP-Discovery  ->	
		<-	DHCP-Offer
DHCP-Request	->
		<-	DHCP-Acknowledgement


**DHCPv4 Ports**:

- UDP port 67 for Server
- UDP port 68 for Client

**IPv6 DHCP process**:

CLIENT				SERVER
--------------------------------------
Solicit		->
		<-	Advertise
Request		->
		<-	Reply

**DHCPv6 Ports**:

- UDP port 546 for Client
- UDP port 547 for Server

**DHCP Relay** is needed when the DHCP server is not on the same subnet, because routers do not forward any broadcast IP packet to interfaces.
**DHCP Relay** Agent allows DHCP messages to be exchanged betwee the DHCP client and the DHCP server residing on different subnet.
**DHCP Option 82** allows Agents to insert cicuit specific information into a request that is being forwarded to a DHCP server.

#### DHCP Starvation Attack

DHCP Starvation Attack is a Denial-of-Service attack on a DHCP server.
Attacker send bogus requests to DHCP server with spoofed MAC address to lease all IP address in DHCP address pool.
Once all IP address is allocated, upcoming users will be unable to obtain IP address or renew the lease.

Tools:

- Dhcpstarv
- Yersinia

#### Rogue DHCP Server

Attacker deploy the rogue DHCP server in the network along with the DHCP starvation attack.
When legitimate DHCP server is in Denial-of-Service attacks, DHCP clients are unable to gain IP address from the legitimate DHCP server.
Upcoming DHCP Discovery (IPv4) and Solicit (IPv6) are replied by the bogus SHCP server with configuration parameter which directs the traffic towards it.

### Defending against DHCP Starvation and Rodue Server Attack

#### DHCP Snooping

DHCP snooping feature identify the only trusted ports from DHCP traffic.
Any access port who tries to reply the DHCP request will be ignored.

#### Port Security

- Limit the learning number of a maximum number of MAC addresses on a port
- Configure violation action, aging time, ...

# ARP Poisoning

## Address Resolution Protocol (ARP)

The Address Resolution Protocol (ARP) is a communication protocol used for discovering the link layer address, such as a MAC address, associated with a given internet layer address, typically an IPv4 address. 
By broadcasting the ARP request with IP address, the switch can learn the associated MAC address information from the reply of the specific host.
If there is no map, or map is unknown, the source will send a broadcast to all node.

#### ARP Spoofing Attack

Attacker send forged ARP packets over Local Area Network (LAN).
In this case, switch will update the attacker's MAC address with the IP address of a legitimate user or server, then start forwarding the packets to the attacker.
Attacker can steal information by extracting it from packets.

ARP Poisoning used for:

- Session hijacking
- Denial-of-Service attacks
- Man-in-the-Middle attacks
- Packet sniffing
- Data interceptions
- VoIP tapping
- Connection reseting
- Stealing passwords

### Defending ARP Poisoning

#### Dynamic ARP Inspection (DAI)

DAI is used with DHCP snooping, IP-to-MAC bindings can be tracked from DHCP transactions to protect against ARP poisoning.

## Spoofing Attacks

### MAC Spoofing/Duplicating

Manipulating the MAC address to impersonate the legitimate user or launch attack such as DoS.
Attacker sniffs the MAC address of users which are active on switch ports and duplicate the MAC address.
This can intercept the traffic and traffic destined to the legitimate user may direct to the attacker.

#### Defend against MAC Spoofing

- DHCP Snooping
- Dynamic ARP Inpection
- Source Guard: monitor and prevent the host to impersonate another host

## DNS Poisoning

### Domain Name System (DNS)

DNS is used in networking to translate human-readable domain names to IP address.
When DNS Server reveives the request, it doesnt have the entry, it generates the query to another DNS Server for the translation and so on.
DNS server having the translation will send back the IP address.

### DNS Poisoning Techniques

When DNS server receives a false entry, it updates its database.
To increase perfomance, DNS servers maintain a cache in which this entry is updated to provide quick resolution of queries.
This false entry causing poison in DNS translation until the cache expires.

#### Intranet DNS Spoofing

Normally performed over Local Area Network (LAN) with switched network.
With the help of ARP poisoning, attacker sniff packet, extarct the ID of DNS requests and reply with fake IP translation directing traffic to the malicious site.

#### Internet DNS Poisoning

Attacker replace the DNS configuration on the target machine.

#### Proxy Server DNS Poisoning

Attacker replace the DNS configuration of the web browser.

#### DNS Cache Poisoning

Attacker exploiting flaws in DNS software, adds or alter the entries.

#### Defending Techniques against DNS Poioning

- Segregate authoritive and recursive resolver
- Query and response verification using DNS Guard
- Restrict external DNS lookup
- Prevent DNS Open Resolver configuration
- Transaction ID randomization
- DNS application inspection configuration
- DNS resolver
- IP Source Guard
- IDS deployment
- Disable recursion
- DNS non-existent domain rate limiting
- Uni-Cast path forwarding
- UDP source port randomization
- DNSSEC

### Sniffing Tools

#### Wireshark

Filters in Wireshark:

- `==`		Equal
- `eq`		Equal
- `!=`		Not equal
- `ne`		Not equal
- `contains`	Contains specified value

## Defending Against Sniffing

- HTTPS instead of HTTP
- SFTP instead if FTP
- Switch instead if Hub
- Port security
- DHCP Snooping
- Dynamic ARP Inspection
- Source guard
- Sniffing detection tools
- Strong encryption protocol

### Sniffing Detection Technique

#### Ping Method

A ping is sent to the suspect IP address with spoofed MAC.
If the NIC is not in promiscuous mode, it will not it will not respond.

#### ARP Method

First, sending non broadcast ARP packet to the suspect, MAC address will be cached if the NIC is in promiscuous mode.

Second, send a broadcast with spoofed MAC, if NIC is in promiscuous mode, it will be able to reply the packet only as it has already learned the actual MAC from sniffed non-broadcast ARP packet.
