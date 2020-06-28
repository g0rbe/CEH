## Terminology

**Footprinting**: collect information about a target network.

**Passive Footprinting**: collect without direct interaction.

**Active Footprinting**: collect with direct interaction.

**Social Network Footprinting**: get information about the target.

**Website Footprinting**: Information about the target through web pages.
	
## Methods

- Examining the web page's source code
- Examining cookies
- Extracting metadata of web sites
- Monitoring website for updates
- Tracking email
- Email header analysis
- Competitive Intelligence Gathering
- Monitoring website traffic
- Tracking online reputation
- WHOIS
- IP geolocation
- DNS footprinting 

## Information collected

- Organization Information (phone numbers, employee details, etc...)
- Relations with other companies
- Network Information (Domains, IPs, etc...)
- System Information (OSes, passwords)

## Objectives of Footprinting:

- **Know Security Posture**: know the security posture of the target organization
- **Reduce Focus Area**: reduce the attackers focus area to a specific range of IP, network, domain names, etc...
- **Identify Vulnerabilities**: identify vulnerabilities in the target system
- **Draw Network Map**: draw a map or outline the target organization's network infrastructure

## Advanced Google Hacking Techniques

Operators:

- `cache:` - Display the web page stored in the google cache
- `link:` - List of web pages that have links to the specified web page
- `related:` - List of web pages that are similar to a specified web page
- `info:` - Presents some information that google has about the particular page
- `site:` - Restrict the results to those websites in the given domain
- `allintitle:` - Restricts the result to those websites with all of the search  keywords in the title
- `intitle:` - Restrict the results to documents containing the search keyword in the title 
- `allinurl:` - Restrict the results to those with all of the search keywords in the URL
- `inurl:` - Restrict the results to documents containing the search keyword in the URL
- `location:` - Find information for a specific location
- `intext:` - Restrict the results to documents containing the search keyword in the content

Find more at [ahrefs blog](https://ahrefs.com/blog/google-advanced-search-operators/).

## WHOIS

Whois databases are maintained by Regional Internet Registries and
contain personal information of domain owner (eg.: email address).

`whois` uses TCP port 43.

Example on Linux:

``` bash
whois danielgorbe.com
```

## DNS footprinting

DNS record types:
- `A`: Points to a host's IP address
- `MX`: Points to a domain's mail server
- `NS`: Points to a host's name server
- `CNAME`: Canonical naming allows aliases to a host
- `SOA`: Indicate authority for domain
- `SRV`: Service records
- `PTR`: Maps IP address to a hostname
- `RP`:  Responsible person
- `HINFO`: Host information record includes CPU type and OS
- `TXT`: Unstructured text records

Example on Linux:

``` bash
dig danielgorbe.com
```

## Traceroute

Trace the path between you and your target computer.

Example on Linux:

``` bash
traceroute danielgorbe.com
```
