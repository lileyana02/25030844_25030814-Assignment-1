# Weevely

Weevely is an open-source command-line tool designed to generate and manage a PHP web shell for remote server control. It is commonly used in cybersecurity testing, especially in penetration testing labs such as Kali Linux environments. The tool works by generating a small PHP file that can be uploaded to a vulnerable web server. Once uploaded, the attacker can connect to that file remotely and execute commands as if they are using the server directly.

The main purpose of Weevely is to maintain access after successfully exploiting a vulnerability. Instead of repeatedly attacking the system, the attacker uploads the Weevely shell and uses it as a backdoor for continuous access.

## Environment details
- Attacker: Kali Linux
- Target: DVWA on a local VM

## Steps
### Step A
<img width="1068" height="151" alt="weevely create file" src="https://github.com/user-attachments/assets/3b880b28-8b1a-41c0-99c0-99a88b812216" />


``` bash 
weevely generate <password> <filename.php>
```
- Firstly, generate a php "agent" file that acts as a remote control endpoint. Then, verify the file exists in the directory.

### Step B
DVWA (Damn Vulnerable Web Application) is an intentionally insecure PHP/MySQL web application designed for security professionals, developers, and students to practice common web attacks legally. It serves as a controlled environment to learn and test vulnerability scanning, exploitation techniques, and defensive security measures.
  
 <img width="1068" height="828" alt="upload doc" src="https://github.com/user-attachments/assets/5f5dfb3e-3ef0-4072-9f35-7aa7d450edc7" />


- In this steps, we used DVWA "File upload" page to upload the PHP agent file that we have created just now. We need to upload testbackdoor.php that we have created previously.

   <img width="1068" height="810" alt="success upload" src="https://github.com/user-attachments/assets/a5557dcd-5190-4553-a149-494162956fa0" />


- Just by click submit, DVWA confirmed the upload was successful.

### Step C - start session (Connect to the uploaded PHP agent)
We need to initiate a seession from Kali terminal to the uploaded PHP agent that we have uploaded to DVWA.

<img width="1068" height="215" alt="access to file with password" src="https://github.com/user-attachments/assets/e86906de-4ae2-4ed7-b358-845387fffd87" />


This demonstrates 'maintaining access'. After the upload, the tester can return later and re-enter via the same endpoint.

### Step D - Feature Demo 1: System/Environment information
Ran the 'system information' capability to identify web server user, working directory, OS version or PHP version.

<img width="1068" height="360" alt="system_info_wee" src="https://github.com/user-attachments/assets/6a3491e3-8452-493a-90aa-368aa258481c" />


```bash
system_info
```
Attackers use this to understand privilege level and plan escalation. Defenders use it to see what information leakage an attacker can confirm post-compromise.

### Step E - Feature demo 2: Remote file listing

In this demo,  we will list the files in the upload directory to confirm what is accessible remotely. 

<img width="1068" height="169" alt="file directory" src="https://github.com/user-attachments/assets/00915ac8-b076-4527-857c-49527f242a9d" />


```bash
file_ls
```
This demonstrate post-access discovery in checking what files exist and where the webroot is.

### Step F - Feature demo 3: Remote File Retrieval

This is used to demonstrate the ability to retrieve files from the remote server after access has been established.

<img width="1146" height="230" alt="download file remotely" src="https://github.com/user-attachments/assets/b4859522-f19f-412a-9168-0f6765dfe5f5" />


```bash
# Example structure (lab environment)
:file_download <remote_file_path> <local_file_path>
```
After successfully establishing a session, a file retrieval capability was tested to download a file from the remote directory to the local Kali machine.

This feature allows the operator to specify:
- The remote file location on the target system
- The local filename where it will be saved

This demonstrates how maintaining access tools can be used not only for command execution but also for data exfiltration within a controlled test environment.


---
## References
Scribd. (n.d.). Tutorial: File upload vulnerabilities. https://www.scribd.com/document/984077152/Tutorial-File-Upload-Vulnerabilities

TutorialsPoint. (n.d.). Kali Linux – Maintaining access. https://www.tutorialspoint.com/kali_linux/kali_linux_maintaining_access.htm

