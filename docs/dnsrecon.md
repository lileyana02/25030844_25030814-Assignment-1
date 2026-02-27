# DNSRecon
### subdomain enumeration
> It is to find all the sub domain names that exist under a main domain name through a dictionary
```
sudo dnsrecon -d example.com -D /usr/share/dnsrecon/namelist.txt -t brt   //Try using the specified dictionary to find all subdomains under example.com
```
<img width="689" height="211" alt="image" src="https://github.com/user-attachments/assets/a58340e7-7875-4c23-8343-0126d863b638" />

### -b
> Search for public information such as subdomains and URLs through the Bing search engine.
```
dnsrecon -d baidu.com -b      //Perform Bing enumeration using standard enumeration.
```
<img width="501" height="152" alt="image" src="https://github.com/user-attachments/assets/01138a9a-f9fc-4012-bd1a-e5804e294b6a" />

### -y 
> Search for public information such as subdomains and URLs through the Yandex search engine.
```
dnsrecon -d baidu.com -y      //Execute Yandex enumeration using standard enumeration
```
<img width="496" height="129" alt="image" src="https://github.com/user-attachments/assets/9de6f78c-b7dd-45cc-965c-9e47509adddd" />

> Advantages: The most comprehensive DNS functionality, multi threading, strong subdomain explosion, perfect AXFR/reverse PTR, and structured results. Suitable for deep DNS reconnaissance, subdomain discovery, and zone transfer testing

- [Dnsrecon全参数详细教程](https://www.bilibili.com/read/cv40056693/?opus_fallback=1)
