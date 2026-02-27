# Tools comparison

## A. Comparison of Reconnaissance Tools

| Tool      | Main Usage | Strength | Limitation |
|------------|----------|----------|------------|
| Recon-ng   | OSINT and information gathering | Organized workspace,have many modules | No port scanning or packet sending |
| Nmap       | Host and port scanning | Accurate service detection, NSE scripts, cross-platform | Limited passive reconnaissance |
| Hping3     | Custom packet testing | Can modify TCP flags, IP | Requires advanced technical knowledge |
| DNSRecon   | DNS enumeration | Detailed DNS records, subdomain discovery, multi-threaded | Limited to DNS-related scanning |

Each reconnaissance tool has a different role. Recon-ng is mainly used to collect public information and store results in a structured way. Nmap is used to discover live hosts, scan open ports, and identify running services. Hping3 focuses on sending custom packets to test firewall behavior and network responses. DNSRecon focuses specifically on DNS enumeration, such as discovering subdomains and testing for zone transfer vulnerabilities. When used together, these tools provide a more complete view of a target system from different angles.

---

## B. Comparison of the Maintaining Access Tool 

| Tool        | Main Method              | Strength | Weakness |
|-------------|--------------------------|----------|----------|
| PowerSploit | Windows system persistence | Strong Windows integration | Windows only, detectable |
| Webshell    | File-based web backdoor  | Simple and easy | File can be detected |
| Weevely     | Encrypted webshell       | More stealthy | Still file-based |
| Dns2tcp     | DNS tunneling            | Bypasses firewall | Slower, DNS monitoring risk |
| Cryptcat    | Encrypted reverse shell  | Lightweight and simple | Needs open ports |

Each maintaining access tool works in a different way. PowerSploit is suitable to be used in Windows systems because it can create persistence through system changes but it is easier to detect with modern security tools. Webshells are simple and allow remote control through a browser but they are depend on a file stored on the server. Weevely is more advanced terminal usage than a basic webshell because it uses encrypted communication which it will making it harder to detect. Dns2tcp is useful in restricted networks since it hides traffic inside DNS but it can be slower and detected through DNS monitoring. Cryptcat provides encrypted remote access however it requires open ports.
