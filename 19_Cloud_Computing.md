Cloud computing is shared pools of configurable computer system resources and higher-level 
services that can be rapidly provisioned with minimal management effort, often over the 
Internet.


Third-party clouds enable organizations to focus on their core businesses instead of expending 
resources on computer infrastructure and maintenance.[1] Advocates note that cloud computing 
allows companies to avoid or minimize up-front IT infrastructure costs. Proponents also claim 
that cloud computing allows enterprises to get their applications up and running faster, with 
improved manageability and less maintenance.

#### Characteristics of Cloud Computing

- Increase users flexibility
- Cost reduction
- Device and location independence
- Distributed storage
- Automated management
- Virtualization
- Measured services

## Cloud Computing Service Models

#### Infrastructure as a Service (IaaS)

The capability provided to the consumer is to provision processing, storage, networks, and other 
fundamental computing resources where the consumer is able to deploy and run arbitrary software, 
which can include operating systems and applications. The consumer does not manage or control 
the underlying cloud infrastructure but has control over operating systems, storage, and 
deployed applications and possibly limited control of select networking components (e.g., host 
firewalls).

#### Platform as a Service (Paas)

The capability provided to the consumer is to deploy onto the cloud infrastructure 
consumer-created or acquired applications created using programming languages, libraries, 
services, and tools supported by the provider. The consumer does not manage or control the 
underlying cloud infrastructure including network, servers, operating systems, or storage, but 
has control over the deployed applications and possibly configuration settings for the 
application-hosting environment.

#### Software as a Service (SaaS)

The capability provided to the consumer is to use the provider’s applications running on a cloud 
infrastructure. The applications are accessible from various client devices through either a 
thin client interface, such as a web browser (e.g., web-based email), or a program interface. 
The consumer does not manage or control the underlying cloud infrastructure including network, 
servers, operating systems, storage, or even individual application capabilities, with the 
possible exception of limited user-specific application configuration settings.

## Cloud Computing Deployment Module 

#### Private Cloud 

The cloud infrastructure is provisioned for exclusive use by a single organization comprising 
multiple consumers (e.g., business units). It may be owned, managed, and operated by the 
organization, a third party, or some combination of them, and it may exist on or off premises. 

#### Community Cloud

The cloud infrastructure is provisioned for exclusive use by a specific community of consumers 
from organizations that have shared concerns (e.g., mission, security requirements, policy, and 
compliance considerations). It may be owned, managed, and operated by one or more of the 
organizations in the community, a third party, or some combination of them, and it may exist on 
or off premises. 

#### Public Cloud

The cloud infrastructure is provisioned for open use by the general public. It may be owned, 
managed, and operated by a business, academic, or government organization, or some combination 
of them. It exists on the premises of the cloud provider.

#### Hybrid Cloud

The cloud infrastructure is a composition of two or more distinct cloud infrastructures 
(private, community, or public) that remain unique entities, but are bound together by 
standardized or proprietary technology that enables data and application portability (e.g., 
cloud bursting for load balancing between clouds).

## NIST Cloud Computing Reference Architecture

- National Institute od Standards and Technology (NIST) presented a high-level conceptual 
reference architecture
- Idetifies the major components and their functions in cloud computing
- Intended to facilitate the understanding of the requirements, uses, characteristics and 
standards of cloud computing

#### Actors 

- **Cloud Consumer** : A person or organization that maintains a business relationship with, and 
uses services from cloud providers
- **Cloud Provider** : A company or individual that delivers cloud computing based services and 
solutions to businesses and/or individuals.
- **Cloud Auditor** : A party that can conduct an idependent assessment of cloud services
- **Cloud Broker** : An entity that manages the use, performance and delivery of cloud services, 
negotiates relationships between providers and consumers
- **Clous Carrier** : An intermediary that provides connectivity and transport of cloud services 
from providers to consumers

## Cloud Compiuting Threads

- Data loss / breach
- Abusing cloud services
- Insecure interfaces / APIs
- Inadequate infrastructure design
- Virtualization level attacks
- Service termination and failure
- Malicious insider
- Hardware failure
- Weak authentication
- Privilege escalation
- Loss of logs

## Cloud Computing Attacks

- Social engineering attacks (password guessing, ...)
- XSS attacks
- DNS attacks (DNS poisoning, domain hijacking, ...)
- SQL injection
- Network sniffing (obtain credentials, cooikes, ...)
- Session hijacking (cookie stealing, ...)
- Cryptanalysis (weak encryption, ...)
- DoS / DDoS 

#### Side Channel Attacks or Cross-Guest Virtual Machine Breaches

- Deploy a malicious virtual machine on the same host
- Take advantage of sharing resources (processor cache, keys, ...)
- Installation can be done by a malicious insider or an impersonated legtitimate user

## Cloud Security

#### Application Layer

- Application firewall (filter and observe tarffic)
- Systems Developement Life Cycle (SDLC)
- Binary Code Anlysis 
- Script anlysis
- Transactional security 

#### Network Layer

- Next Generation IPS / IDS (NGIPS / NGIDS)
- Firewalls
- DNSSec
- Anti-DDoS

#### Information

- Provide confidentiality and integrity 
- Data Loss Prevention (DLP)
- Content Management Framework (CMF)

#### Trusted Computing

- Root of Trust (RoT) is estabilished by validating each component of hardware and software to ensure that only trusted hardware 
and software can be used

#### Computer and Storage

- Host-based IPS / IDS  (HIDS/HIPS)
- Integrity check
- File system monitoring
- Log file analysis
- Connection analysis
- Storage encryption

#### Physical Security

- Physical protection is priority
- Protect against theft, unauthorized physical access, environmental impact (rain, earthquake, power failure, ...)

## Responsibilities in Cloud Security

#### Cloud Service Provider

- Web Application Firewall (WAF)
- Real Traffic Grabber (RTG)
- Firewall
- Data Loss Prevention (DLP)
- Intrusion Prevention System (IPS)
- Secure Web Gateway (SWG)
- Application Security (App Sec)
- Virtual Private Network (VPN)
- Load Balancer
- CoS / QoS
- Trusted Platform Module
- Netflow

#### Cloud Service Consumer

- Public Key Infrastructure (PKI)
- Security Developement Life Cycle (SDLC)
- Firewall
- Encryption
- Intrusion Prevention System (IPS)
- Application Security
- Virtual Private Network (VPN)

## Cloud Computing Countermeasures and Security Considerations

- Software Configuration Management (SCM)
- Disaster Recovery Plan
- Load Balancing
- Data Integrity
- Patching and updates
- SSL
- Cryptography implementation
- Reliability
- Quality of Service (QoS)
- Monitoring
- Service Level Agreement (SLA)
