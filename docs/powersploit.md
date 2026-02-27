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

<img width="972" height="226" alt="image" src="https://github.com/user-attachments/assets/0c78f176-de2b-496d-b98c-1d7795d7f15f" />

The available commands are verified using:

```powershell
Get-Command -Module Recon
```

<img width="912" height="173" alt="image" src="https://github.com/user-attachments/assets/eb0eb638-a14b-4d11-9101-4c8619f7f5bb" />

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
Invoke-ReverseDnsLookup performs reverse DNS resolution, which maps an IP address to its associated hostname using PTR records in DNS.

This technique is part of passive reconnaissance and is used to identify the ownership of an IP address, determine hosting providers,discover infrastructure naming conventions

When executed against a public IP (8.8.8.8), the tool successfully resolved the hostname dns.google, confirming that the IP belongs to Google’s DNS infrastructure.


### Feature 2: Get-ComputerDetail
command executed:
```powershell
Get-ComputerDetail
```

<img width="995" height="702" alt="Screenshot 2026-02-26 082635" src="https://github.com/user-attachments/assets/cc2496bb-69e7-4431-b738-021d4625dee4" />

The output included:
- LogonEvent4624 (Successful logon events)
- LogonEvent4648 (Explicit credential logon attempts)
- Security log data
- PowerShell script execution logs
  
Get-ComputerDetail extracts forensic relevant information from Windows event logs and system configurations. It provides logged-in user details,account authentication history,source network addresses,powerShell activity records


### Feature 3 : Invoke-Portscan

<img width="976" height="42" alt="Screenshot 2026-02-26 075415" src="https://github.com/user-attachments/assets/f76f6668-7ba6-42b9-b9b6-47dabf7d6182" />


command executed:
```powershell
Invoke-Portscan -Hosts <ip> -Ports "1-200"
```
Invoke-Portscan performs TCP port scanning to identify open services on a target host. It attempts connections across a defined range of ports and reports which ports are open.


