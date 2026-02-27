# Webshells
A web shell is a malicious script uploaded to a vulnerable web application that allows remote command execution through a web browser. It acts as a backdoor, enabling an attacker to interact with the underlying operating system via HTTP requests. In penetration testing, web shells are commonly used to demonstrate the impact of insecure file upload vulnerabilities.

Damn Vulnerable Web Application (DVWA) was used to simulate an insecure file upload scenario. It used to demonstrate how improper input validation can lead to remote command execution and unauthorized system access.

## Lab environment
- Attacker Machine: Kali Linux
- Target Machine: Metasploitable 2
- Web Application: DVWA

## Features Demo
### Step 1: Creating the PHP Script in Kali
The PHP file was created locally in Kali Linux before being uploaded to the vulnerable web application.

<img width="909" height="136" alt="type in" src="https://github.com/user-attachments/assets/bc6a4c7c-906f-43bf-bd29-908157d32798" />

The script allows system command execution via a URL parameter.
This type of script enables dynamic execution of operating system commands passed through the browser.

The script performs the following functions:
1. It retrieves a value from the URL parameter.
2. It passes that value to the operating system command interpreter.
3. It displays the output directly in the browser.

### Step 2: Access DVWA login page
The DVWA login page was accessed via:
```bash http://<ip>/dvwa/login.php```

### Step 3: Set Security Level to Low

<img width="990" height="669" alt="security" src="https://github.com/user-attachments/assets/44afb085-2ee9-458d-8b33-5aa46ba2961b" />


The DVWA security level was changed to "Low" to allow exploitation of file upload vulnerability. This configuration reduces input validation and simulates a poorly secured web application.

### Step 4: Upload web shell
In file upload module, shell.php file was selected and uploaded.

<img width="906" height="683" alt="upload" src="https://github.com/user-attachments/assets/2b7da933-44d3-46c2-8b93-3eab08575573" />

<img width="931" height="734" alt="successupload" src="https://github.com/user-attachments/assets/8a27dc82-7f38-4c0c-ac9f-adeec3b5f380" />


This indicates the server accepted and stored executable PHP code without proper validation.


### Step 5 - Execute Commands via Browser
After uploading, the shell was accessed through:
```bash
http://<<ip>/dvwa/hackable/uploads/shell.php
```
Commands were executed via the cmd parameter.
  - feature 1: identify user
    
<img width="990" height="141" alt="successsnap" src="https://github.com/user-attachments/assets/baaae83d-44cb-45a7-8d44-7d6c3a93b46e" />


  Output:
  ```bash
  www-data
  ```
  This confirms the command was executed on the server and shows the web server process user.

  - Feature 2: Display Current Directory
    
    <img width="990" height="149" alt="pwd" src="https://github.com/user-attachments/assets/1b9dfd1a-27bf-4b8f-a82d-f2ec2cf7eb08" />

    Output:
  ```bash
  /var/www/dvwa/hackable/uploads
  ```
  This confirms filesystem access via the web shell.

  - Feature 3 List files in directory
    
  <img width="990" height="148" alt="ls -la" src="https://github.com/user-attachments/assets/c3b55602-1173-4e00-aec2-03c54abd3460" />

 <img width="669" height="157" alt="cmd=ls" src="https://github.com/user-attachments/assets/701bb49e-d958-4090-95bc-f1f61418b0fa" />
 

  Output shows:
```bash
shell.php
dvwa_email.png
```
  This demonstrates the ability to enumerate server files.


---
## References
Dodd, S. (2017). DVWA file upload vulnerability. https://spencerdodd.github.io/2017/03/05/dvwa_file_upload/

