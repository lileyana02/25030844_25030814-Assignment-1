# Tools comparison


# Recon-ng
### One stop passive+active reconnaissance, rich modules, and result storage; Pure reconnaissance, no port scanning, no packet sending, no DNS deep enumeration.
# Nmap
### Used for host discovery, port scanning, and service/system identification. Versatile, stable, strong NSE script, cross platform, but weak passive reconnaissance.
# Hping3
### Used for custom packet construction, firewall detection, and stress testing. TCP flags, source IP, shards can be changed arbitrarily TTL， Strong bypassing ability.
# DNSRecon
### DNS specialized reconnaissance tool, fully functional, multi-threaded, capable of dictionary explosion.



## Comparison of the Maintaining Access Tool 

| Tool        | Main Method              | Strength | Weakness |
|-------------|--------------------------|----------|----------|
| PowerSploit | Windows system persistence | Strong Windows integration | Windows only, detectable |
| Webshell    | File-based web backdoor  | Simple and easy | File can be detected |
| Weevely     | Encrypted webshell       | More stealthy | Still file-based |
| Dns2tcp     | DNS tunneling            | Bypasses firewall | Slower, DNS monitoring risk |
| Cryptcat    | Encrypted reverse shell  | Lightweight and simple | Needs open ports |

Each maintaining access tool works in a different way. PowerSploit is suitable to be used in Windows systems because it can create persistence through system changes but it is easier to detect with modern security tools. Webshells are simple and allow remote control through a browser but they are depend on a file stored on the server. Weevely is more advanced terminal usage than a basic webshell because it uses encrypted communication which it will making it harder to detect. Dns2tcp is useful in restricted networks since it hides traffic inside DNS but it can be slower and detected through DNS monitoring. Cryptcat provides encrypted remote access however it requires open ports.
