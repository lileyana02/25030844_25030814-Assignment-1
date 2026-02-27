# DNSRecon
DNSRecon is a DNS enumeration tool used during the reconnaissance phase of penetration testing. It gathers detailed information about a domain, including DNS records, name servers, subdomains, and potential misconfigurations.
DNSRecon helps to understand how a domain is structured and whether sensitive DNS data is exposed publicly.

## Features Demo

### Feature 1 : Standard DNS Record Enumeration
command:

```bash
dnsrecon -d example.com
```

<img width="1074" height="668" alt="Standard DNS Record Enumeration" src="https://github.com/user-attachments/assets/9ccca017-59ba-4c92-b75b-c20844235274" />

This command performs general DNS enumeration against the target domain. It collects publicly available DNS records including:
1. SOA (Start of Authority)
2. NS (Name Servers)
3. A Records
4. AAAA Records
5. TXT Records
6. DNSSEC information

This demonstrates that DNSRecon successfully retrieves publicly accessible DNS configuration details. Such information helps identify:

- Hosting providers
- Email configuration
- IPv4 and IPv6 addresses
- Security configurations (SPF, DKIM, DNSSEC)

### Feature 2 : Zone Transfer Test (AXFR)
```bash
dnsrecon -d example.com -t axfr
```

<img width="1074" height="1239" alt="Zone Transfer Test (AXFR)" src="https://github.com/user-attachments/assets/d8311888-4909-4b24-b5a2-e2a8aec8b647" />

The AXFR option attempts a DNS zone transfer from the target’s name servers. A successful zone transfer would expose all DNS records of the domain.
The output shows:
- Port 53 is open.
- Zone Transfer Failed (FORMERR).
- Port 53 TCP is being filtered for some servers.

The failure indicates that the name servers are properly configured to prevent unauthorized zone transfers. This is a secure configuration. If the transfer had succeeded, it would have revealed internal subdomains, development environments, internal IP addresses.

### Feature 3 : Subdomain Brute Force

```bash
dnsrecon -d example.com -t brt
```
<img width="1074" height="175" alt="Subdomain Brute Force" src="https://github.com/user-attachments/assets/583bb986-77b5-4108-b9f6-c7ff2a49636a" />

The brute-force mode attempts to discover hidden subdomains using a predefined wordlist.
Subdomain brute forcing identifies:
- Public facing services
- Forgotten test environments
- Administrative panels
- API endpoints
even when zone transfer fails, brute force can still reveal accessible subdomains.

---
## References
TechMindXperts. (n.d.). What is DNSRecon? Full guide with examples. Medium. https://medium.com/@techmindxperts/what-is-dnsrecon-full-guide-with-examples-355aba308332

HackerCool Magazine. (n.d.). Complete guide to DNSRecon. https://www.hackercoolmagazine.com/complete-guide-to-dnsrecon/
