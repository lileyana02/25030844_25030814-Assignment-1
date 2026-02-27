# Hping3
> This is an open-source custom TCP/IP packet generation and analysis tool, often referred to as the "Advanced Ping". Its core advantage lies in its fine control over protocol fields and support for multiple protocols. It is widely used for network diagnosis, security auditing, and stress testing.
### Customize ICMP Ping Scan
```
sudo hping3 -1 -c 5 -d 100 <IP>    //Specify ICMP protocol to send 5 packets of 100kb size
```
<img width="876" height="264" alt="image" src="https://github.com/user-attachments/assets/8d023737-5e9d-46b8-8994-e963780b8f5c" />

### TCP port scanning
```
sudo hping3 -S -p 80 -c 10 <IP>        //Scan port 80
```
<img width="628" height="121" alt="image" src="https://github.com/user-attachments/assets/f86631d6-ef83-40ff-a788-9e36e0b50be5" />

### SYN flood attack
```
sudo hping3 -S -p 80 --flood <IP>      //
```
<img width="623" height="96" alt="image" src="https://github.com/user-attachments/assets/68b35999-021e-42de-8f34-ebda382cd602" />

> Advantages: Bottom layer outsourcing, custom flag placement, source IP forgery, sharding, firewall bypass, stress testing. Suitable for firewall rule verification, protocol stack fingerprinting, bypassing ban ping, fine port detection, and performance testing

- [hping3全参数详细教程](https://blog.csdn.net/qq_24305079/article/details/144963291)
