# Dns2tcp

Dns2tcp is a tunneling utility that encapsulates TCP traffic inside DNS queries and responses. In practice, this technique can be used when direct outbound connections (SSH or other TCP ports) are blocked but DNS traffic is still allowed. From a penetration testing perspective, Dns2tcp helps demonstrate how DNS can be abused as a communication channel if network monitoring and DNS controls are weak.

##Features demo
## Step-by-Step (Documentation Flow)

### Step A - Verify tool availability
In this lab, the first step is to confirm whether the required binaries exist on each VM .  

<img width="694" height="119" alt="intro_install" src="https://github.com/user-attachments/assets/b50cafc4-0bdd-4925-a650-610bf0685126" />

This confirms  both server and client components are installed.

### Configuration File demo
### Step B - Create Configuration file

```bash
nano dns2tcp.conf
```

Configuration content:

```conf
domain=example.local
resource=ssh:127.0.0.1:22
```
Domain defines the DNS domain used for the tunnel communication.
Resource maps a TCP service to a DNS-accessible identifier.

This demonstrates how DNS2TCP associates a TCP service with DNS queries.

<img width="734" height="542" alt="create conf" src="https://github.com/user-attachments/assets/0568ea9e-e77b-45a9-b655-9818f1befba9" />

#### Feature 1: Client-Server Architecture
DNS2TCP operates using:
- dns2tcpd use server daemon
- dns2tcpc  use client tool.
This separation enables remote encapsulation of TCP traffic over DNS. This architecture allows structured tunneling control.

#### Feature 2 : Resource Mapping via Configuration

DNS2TCP uses configuration-based resource mapping to define which services are tunneled.
This demonstrates:
- Customizable service exposure
- Controlled tunnel endpoints
- Structured DNS-to-TCP encapsulation

#### Feature 3 : DNS-Based Data Encapsulation
DNS2TCP encapsulates TCP packets inside DNS queries and responses.

Because DNS traffic:
- Is typically allowed on port 53
- Is rarely deeply inspected
- Is considered 'trusted' traffic

It may be abused as a covert communication channel.


