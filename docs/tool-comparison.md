# Tools comparison


# Recon-ng
### One stop passive+active reconnaissance, rich modules, and result storage; Pure reconnaissance, no port scanning, no packet sending, no DNS deep enumeration.
# Nmap
### Used for host discovery, port scanning, and service/system identification. Versatile, stable, strong NSE script, cross platform, but weak passive reconnaissance.
# Hping3
### Used for custom packet construction, firewall detection, and stress testing. TCP flags, source IP, shards can be changed arbitrarily TTL， Strong bypassing ability.
# DNSRecon
### DNS specialized reconnaissance tool, fully functional, multi-threaded, capable of dictionary explosion.



## Maintaining Access Tool Comparison

| Tool        | Main Method              | Strength | Weakness |
|-------------|--------------------------|----------|----------|
| PowerSploit | Windows system persistence | Strong Windows integration | Windows-only, detectable |
| Webshell    | File-based web backdoor  | Simple and easy | File can be detected |
| Weevely     | Encrypted webshell       | More stealthy | Still file-based |
| Dns2tcp     | DNS tunneling            | Bypasses firewall | Slower, DNS monitoring risk |
| Cryptcat    | Encrypted reverse shell  | Lightweight and simple | Needs open ports |
