# Recon-ng
> Due to the fact that Due to the fact that **Rrcon-ng V5** does not come with built-in modules, all functions need to be downloaded from the  does not come with built-in modules, all functions need to be downloaded from the **marketplace**..

```
marketplace install all
```
<img width="551" height="95" alt="image" src="https://github.com/user-attachments/assets/39a0fb1d-0cfd-4447-8539-5fccac76f85a" />

### Collect subdomains
> 
```
modules search bing    //Search for modules related to Bing
```
<img width="490" height="163" alt="image" src="https://github.com/user-attachments/assets/d02bf7e4-c091-4470-86bf-660e126d9ad9" />

```
module load <Module Name>  
```
```
option set SOURCE example.com
```
```
run
```
<img width="628" height="144" alt="image" src="https://github.com/user-attachments/assets/51c9c1bc-cff6-48d7-a998-4fff59511260" />

### certificate_transparency
> This is a public and auditable TLS certificate supervision mechanism that records all legitimate SSL/TLS certificates in a public log that is only appended and cannot be tampered with, allowing anyone to verify and quickly detect malicious/mis issued certificates, preventing man in the middle attacks.
```
module load recon/domains-hosts/certificate_transparency
```
```
option set SOURCE example.com
```
```
run
```

<img width="661" height="126" alt="image" src="https://github.com/user-attachments/assets/5cfebfd8-216f-4cf2-9e14-b3b60b9e2f93" />

### DNS resolution
> Convert the domain name to the corresponding IP address so that network devices can find the target host.
```
module load recon/hosts-hosts/resolve
```
```
run
```
<img width="524" height="35" alt="image" src="https://github.com/user-attachments/assets/e4155220-4ab5-460c-8cab-a9668e34fc76" />

> Advantages: Modular, data linkage, reporting, API integration, automated workflows
- [渗透测试RECON-NG介绍](https://blog.csdn.net/weixin_42952508/article/details/124443273)
