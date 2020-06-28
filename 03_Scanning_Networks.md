## Protocols

These definitions is **must-know** !

- [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) (Transmission Control Protocol)
- [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol) (User Datagram Protocol)
- [ARP](https://www.tummy.com/articles/networking-basics-how-arp-works/)
- [ICMP](https://www.webopedia.com/TERM/I/ICMP.html)
- Ping Sweep: mass ICMP echo (ping) message
- [SSDP](https://wiki.wireshark.org/SSDP)
- [DHCP](https://www.lifewire.com/what-is-dhcp-2625848)
- [DNS](https://dyn.com/blog/dns-why-its-important-how-it-works/)
- [UPnP](https://en.wikipedia.org/wiki/Universal_Plug_and_Play)


## TCP Flags

- `SYN`: Initiates a connection between two hosts to facilitate communication
- `ACK`: Acknowledge the receipt of a packet
- `URG`: Indicates that the data contained in the packet is urgent and should process it immediately
- `PSH`: Instructs the sending system to send all buffered data immediately
- `FIN`: Tells te remote system about the end of the communication. In essence, this gracefully closes the connection
- `RST`:  Reset a connection

## Three-way handshake

- Establish a TCP connection

| Computer1 | Direction | Computer2 |
|:---------:|:---------:|:---------:|           
|    SYN    |    ->     |           |
|	        |    <-     |  SYN+ACK  |
|    ACK    |    ->     |           |

## OSI Model

| Layer |       Name         | Example protocols |
|:-----:|:------------------:|:-----------------:|
|   7   | Application layer  |    HTTP, SNMP     |
|   6   | Presentation layer |    MIME, ASCII    |
|   5   | Session layer      |    SOCKS, NetBIOS |
|   4   | Transport layer    |    TCP, UDP       |
|   3   | Network layer      |    IP, ICMP       |
|   2   | Data link layer    |    MAC, ARP       |
|   1   | Physical layer     |  ethernet, Wi-Fi  |

## TCP/IP Model

| Layer |       Name         | Example protocols |
|:-----:|:------------------:|:-----------------:|
|   4   | Application layer  |    HTTP, SNMP     |
|   3   | Transport layer    |    TCP, UDP       |
|   2   | Internet layer     |    IP, ICMP       |
|   1   | Link layer         |    ARP, MAC       |

## Scanning Techniques

### TCP Connect() / Full Open Scan

- Three-way handshake
- Completed connection
- Logged and detected
- Don't need ROOT
- nmap: `-sT`

Open port:

| Attacker  | Direction | Target    |
|:---------:|:---------:|:---------:|
|    SYN    |    ->     |           |
|           |    <-     |  SYN+ACK  |
|    ACK    |    ->     |           |
|    RST    |    ->     |           |

Closed port:

| Attacker  | Direction | Target    |
|:---------:|:---------:|:---------:|
|    SYN    |    ->     |           |
|           |    <-     |    RST    |

Example:

``` bash
nmap -sT danielgorbe.com
```

### Stealth Scan / Half-Open Scan

- Half Three-way Handshake
- Nmap: `-sS`

Open Port:

| Attacker  | Direction | Target    |
|:---------:|:---------:|:---------:|
|    SYN    |    ->     |           |
|           |    <-     |  SYN+ACK  |
|    RST    |    ->     |           |

Closed port:

| Attacker  | Direction | Target    |
|:---------:|:---------:|:---------:|
|    SYN    |    ->     |           |
|           |    <-     |    RST    |

Example:

``` bash
nmap -sS danielgorbe.com
```

### Inverse TCP Flag Scanning

- Send TCP probe with TCP flags (i.e. FIN, URG, PSH, without flag)
- Xmas and Null scan

#### Xmas Scan

- PSH+URG+FIN flag or ALL flag
- Create abnormal situation
- Nmap: `-sX`

Open port:

|  Attacker   | Direction | Target      |
|:-----------:|:---------:|:-----------:|
| FIN+URG+PSH |    ->     |             |
|             |    <-     | No response |

Closed port:

|  Attacker   | Direction | Target      |
|:-----------:|:---------:|:-----------:|
| FIN+URG+PSH |    ->     |             |
|             |    <-     |    RST      |

Example:

``` bash
nmap -sX danielgorbe.com
```

#### NULL Scan

- No flag
- Easy to detect
- Nmap: `-sN`

Open port:

|  Attacker   | Direction | Target      |
|:-----------:|:---------:|:-----------:|
|     NULL    |    ->     |             |
|             |    <-     | No response |

Closed port:

|  Attacker   | Direction | Target      |
|:-----------:|:---------:|:-----------:|
|     NULL    |    ->     |             |
|             |    <-     |    RST      |

Example:

``` bash
nmap -sT danielgorbe.com
```

### FIN Scan

- FIN scan work with RFC-793 based TCP/IP (before Win XP)
- Only FIN flag
- Probably pass firewalls
- Nmap: `-sF`

Open port:

|  Attacker   | Direction | Target      |
|:-----------:|:---------:|:-----------:|
|     FIN     |    ->     |             |
|             |    <-     | No response |

Closed port:

|  Attacker   | Direction | Target      |
|:-----------:|:---------:|:-----------:|
|     FIN     |    ->     |             |
|             |    <-     |    RST      |

Example:

``` bash
nmap -sF danielgorbe.com
```

### ACK Flag probe scanning

- Only ACK flag
- The response is always an RST
- Examine the RST header (i.e. TTL, WINDOW), the decide if port open or not
- Help identify filtering system: RST mean no firewall, No response mean there is a firewall
- Nmap: `-sA`

Example:

``` bash
nmap -sA danielgorbe.com
```

### IDLE / IPID Header scan

- Remaining low profile
- Scanning done by a zombie
- Based on Full Open scan
- The unsolicited SYN+ACK packet is ignored or responded with RST
- Every IP packet has Fragment Identification Number (IPID)
- OS increment IPID for each packet
- Nmap: `-sI <zombie host[:probeport]>`
- *Explanation* on Nmap's [website](https://nmap.org/book/idlescan.html)

### UDP Scan

- Connectionless protocol
- nmap: `-sU`

Open port:

|      Attacker       | Direction | Target      |
|:-------------------:|:---------:|:-----------:|
|    UPD Port probe   |    ->     |             |
|                     |    <-     | No response |

Closed port:

|      Attacker       | Direction |        Target         |
|:-------------------:|:---------:|:---------------------:|
|    UPD Port probe   |    ->     |                       |
|                     |    <-     | ICMP Port Unreachable |

Example:

``` bash
nmap -sA danielgorbe.com
```

### IDS / IPS evasion

- Packet fragmentation:
- Nmap: `-f`
- The IDS have to reassemble the packets to detect an attack
- Sending packet with delay

Example:

``` bash
nmap -f danielgorbe.com
```

### OS Fingerprinting

#### Active OS fingerprinting

- Nmap: `-O`
- Send TCP and UDP packets and observe the response from the host

Example:

``` bash
nmap -O danielgorbe.com
```

#### Passive OS fingerprinting

- Detail assessment of the traffic (TTL, TCP Window Size)
- Common values:

|     OS       |  TTL  |  TCP Window Size  |
|:------------:|:-----:|:-----------------:|
|   Linux      |  64   |        5840       |
|  Windows XP  |  128  |        65535      |
| Windows 2008 |  128  |        8192       |
|   FreeBSD    |  64   |        5840       |

- More values [here](https://subinsb.com/default-device-ttl-values/)

### Banner Grabbing

- Determine the service
- Typically uses Telnet

Example:

``` bash
nmap -sV danielgorbe.com
```
## Proxy

- System between the attacker and the target
- Hiding source IP address
- Impersonating
- Hide identity

### Proxy chaining

- Using multiple proxy server
- Most used proxy chains: Tor

## Spoofing IP address

- Modify packet header
- nmap has a *decoy* scan option, this option send packets with spoofed source IP to cloak the your address.

Example:

``` bash
nmap -D 192.168.1.1,192.168.1.2 danielgorbe.com
```

This option sends 3 packets with source IP:

1. 192.168.1.1
2. 192.168.1.2
3. Your IP

### Detect Spoofing

- Direct TTL probe (on same subnet)
- IP Identification Number
