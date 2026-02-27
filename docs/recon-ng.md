# Recon-ng

Recon-ng is a web reconnaissance framework written in Python that automates open-source intelligence (OSINT) gathering. It provides a modular structure similar to Metasploit, where users load modules to collect information about domains, hosts, companies, and SSL certificates.

Recon-ng is primarily used during the reconnaissance phase of penetration testing to gather publicly available information without directly attacking the target.

## Steps

### Step 1 : Launch Recon-ng
```bash
recon-ng
```
<img width="798" height="489" alt="launch" src="https://github.com/user-attachments/assets/6ab51d1a-5df8-4b92-9650-a2fa6e5fbc12" />

This confirms Recon-ng is properly installed.

### Step 2 : Create and Manage Workspace

Recon-ng uses workspaces to separate projects.

<img width="798" height="200" alt="listworkspaces" src="https://github.com/user-attachments/assets/8e60b291-d5e7-4b56-a7d3-c6768427bff1" />

1. Create Workspace
```bash
workspaces create cyberdemo
 ```
3. List Workspaces
```bash
workspaces list
 ```
5. Load Workspace
```bash
workspaces load cyberdemo
```

A workspace acts as a project folder. All collected data is stored inside that workspace database.

### Step 3 : Insert Target Domain into Database
Before running modules, it is must to insert the domain manually.

Command:
```bash
db insert domains
```
<img width="798" height="315" alt="db" src="https://github.com/user-attachments/assets/de74b5fb-c157-4f3d-baa0-9dad9dac4da9" />

Verify the domain added using command :
```bash
show domains
```

Recon-ng modules rely on database inputs. If the domain is not inserted, modules cannot run.

### Step 4 : Install and Load Hackertarget Module

Search Module
```bash
marketplace search hackertarget
```

<img width="2160" height="1088" alt="marketplace search" src="https://github.com/user-attachments/assets/43cf3580-d50c-40c3-8532-e82c521757ad" />

Install Module
```bash
marketplace install hackertarget
```

Load Module
``` bash
 modules load recon/domains-hosts/hackertarget
```

<img width="798" height="600" alt="install,help hackertarget_cyber" src="https://github.com/user-attachments/assets/73b4a180-467f-4546-9a36-dcb1b630cd0d" />


### Step 5 : Configure Module options
Show Options
```bash
show options
```
Set Target
```bash
options set SOURCE example.com
```
Run Module
```bash
run
```


## Features

### Feature 1: Host Discovery via HackerTarget

<img width="798" height="600" alt="showhosts_ssl" src="https://github.com/user-attachments/assets/4a3c6085-dbca-4a5c-a6c8-18e68bbd2bc6" />

The module discovered:
- example.com = 104.18.27.120
- www.example.com = 104.18.26.120

This module queries external intelligence sources to identify domain IP addresses, associated hostnames, basic host information.

### Feature 2 : SSL Information Gathering

<img width="798" height="396" alt="ssl info" src="https://github.com/user-attachments/assets/7a1d9080-98fa-4939-a384-aeb9eb6ef098" />


This module collects SSL certificate information including
- Certificate issuer
- Certificate subject
- Expiration details
- Encryption type

### Feature 3 : Reporting Module (HTML Export)

<img width="798" height="155" alt="reports" src="https://github.com/user-attachments/assets/a577f8a6-ea6f-4427-b141-7a263bbed56c" />

First, install
```bash
marketplace install reporting/html
modules load reporting/html
```

then:
```bash
options set FILENAME recon_report.html
```

The reporting module exports reconnaissance results into a structured HTML report. Recon-ng demonstrates how attackers collect intelligence without sending malicious traffic. Since it relies on OSINT sources, traditional firewalls cannot detect it easily.

---
## References
HackerTarget. (n.d.). Recon-ng tutorial. https://hackertarget.com/recon-ng-tutorial/
