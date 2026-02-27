# Nmap
>It can automatically recognize, operate system fingerprint recognition, NSE (Nmap scripting engine), intuitive results, and is suitable for asset mapping. Very suitable for routine port scanning, service enumeration, preliminary vulnerability screening, and internal network topology analysis.
### Host alive scan
```
nmap -sn 192.168.1.0/24    //Detecting the online status of devices corresponding to IP addresses within a specified network segment
```
<img width="568" height="364" alt="image" src="https://github.com/user-attachments/assets/be9a152b-60c7-4cc0-8763-22ebbe4d8f02" />

### Common port scanning
```
nmap -sS -p 1-1000 <IP>  //Detect the switch status of the specified port number
```
<img width="518" height="213" alt="image" src="https://github.com/user-attachments/assets/f9d34dd3-99a1-498a-974b-6b63d3eb343e" />

### Service version and system identification scanning
```
nmap -sV -O <IP>    //Instructions for deep recognition of target host information
```
<img width="1075" height="371" alt="image" src="https://github.com/user-attachments/assets/be96decc-17de-48ed-afab-bc586d67ee8a" />

> Advantages: Automatic recognition, OS fingerprinting, NSE, intuitive results, suitable for asset mapping. Ideal for routine port scanning, service enumeration, initial vulnerability screening, and internal network topology

- [Nmap完整使用教程](https://blog.csdn.net/wrjhs/article/details/147080972)
