# Powersploit
---
PowerSploit is an open-source PowerShell based post-exploitation framework designed for penetration testing and red team operations within Windows environments. It provides a collection of modules that support reconnaissance, privilege escalation, credential harvesting, persistence, and code execution.


##Lab Environment
- Target Machine: Windows Virtual Machine
- PowerSploit framework downloaded locally
- PowerShell executed with administrative privileges

The Recon module was imported using :

```powershell
cd .\Recon\ Import-Module .\Recon.psd1
```
<img width="972" height="226" alt="Screenshot 2026-02-27 120353" src="https://github.com/user-attachments/assets/5d6bc13a-707c-485f-945b-8d1ec77d56a0" />

The available commands are verified using:

```powershell
Get-Command -Module Recon
```

<img width="912" height="173" alt="Screenshot 2026-02-27 120237" src="https://github.com/user-attachments/assets/343e5504-ea2f-4e0a-8c17-42d3e5f472ce" />

## Features demo
### Feature 1: Invoke-ReverseDnsLookup
Command Executed:

``` powershell
Invoke-ReverseDnsLookup 8.8.8.8
```

Output :
```powershell
IP        HostName
8.8.8.8   dns.google
```

<img width="1001" height="182" alt="Screenshot 2026-02-26 082150" src="https://github.com/user-attachments/assets/edd48a98-04e4-474f-be8e-f82827a04e8a" />

Invoke-ReverseDnsLookup performs reverse DNS resolution, which maps an IP address to its associated hostname using PTR records in DNS.

This technique is part of passive reconnaissance and is used to identify the ownership of an IP address, determine hosting providers,discover infrastructure naming conventions

When executed against a public IP (8.8.8.8), the tool successfully resolved the hostname dns.google, confirming that the IP belongs to Google’s DNS infrastructure.


### Feature 2: Get-ComputerDetail
command executed:
```powershell
Get-ComputerDetail
```

<img width="995" height="702" alt="Screenshot 2026-02-26 082635" src="https://github.com/user-attachments/assets/640e0095-19c9-4b64-ba17-e54882eb840b" />


The output included:
- LogonEvent4624 (Successful logon events)
- LogonEvent4648 (Explicit credential logon attempts)
- Security log data
- PowerShell script execution logs
  
Get-ComputerDetail extracts forensic relevant information from Windows event logs and system configurations. It provides logged-in user details,account authentication history,source network addresses,powerShell activity records


### Feature 3 : Invoke-Portscan

<img width="976" height="42" alt="Screenshot 2026-02-26 075415" src="https://github.com/user-attachments/assets/d787c454-ec80-4e8a-a0ad-930713f9fb13" />

command executed:
```powershell
Invoke-Portscan -Hosts <ip> -Ports "1-200"
```
Invoke-Portscan performs TCP port scanning to identify open services on a target host. It attempts connections across a defined range of ports and reports which ports are open.


---
## References
Fox, N. (n.d.). PowerSploit usage & detection. https://neil-fox.github.io/PowerSploit-usage-&-detection/

OpenAI. (2024). ChatGPT (February 27 version) [Large language model]. https://chat.openai.com/

