# CODTECH_TASK2
## WEB APPLICATION PENETRATION TESTING
## Personal information 
- Name : Premkumar Soni
- Company : CODTECH IT SOLUTIONS PVT.LTD
- ID : CTO8DBS
- Domain : Cyber Security & Ethical Hacking
- Duration: 20th Dec 2024 To 20th Jan 2025
- Mentor : Muzammil Ahmed

## Overview 
- Web Application Penetration Testing involves identifying and exploiting security vulnerabilities in web applications to ensure they are secure against potential attacks. This process focuses on vulnerabilities like SQL injection, cross-site scripting (XSS), and insecure authentication mechanisms.
## objective 
- Identify vulnerabilities
- Exploit weaknesses to understand potential attacks
- Recommend remediation to enhance security
## Tools used in web application Testing
- sqlmap
- burpsuite
- nmap
- nikto
- dirb
- owasp zap
- Metasploit Framework
- nessus etc.
## focus vulnerabilities 
- cross site scripting (XSS)
- SQL injection
- insecure authentication
- open redirect etc.
## Performed Task
### Details of site where we performed the web application Testing
- **Site Name** : http://testphp.vulnweb.com
- **IP address** : 44.228.249.3
- **Web server** : HTTPServer[nginx/1.19.0]
- **technology used** : 1. PHP[5.6.40-38+ubuntu20.04.1+deb.sury.org+1] , 2. Script[text/JavaScript]
- **Port** : 80 [http] open
### Performed Testing on testphp.vulnweb.com
***1. XSS Vulnerability***

- step 1 : Now first open the site and write xss payload on serachbar.
```payload
<script>alert("XSS vulnerability found")</script>
```
![image](https://github.com/user-attachments/assets/b622d740-4a3c-42c9-8654-8196b1e75555)

- step 2 : click on the go or tap ENTER. Now here you see we find XSS vulnerability in testphp.vulnweb.com site.

![image](https://github.com/user-attachments/assets/93508085-ec0d-480b-82e8-611469ed5891)

***2. SQL injection Vulnerability***

- Step 1 : In first step first we found the phpid of ***testphp.vulnweb.com*** site.
```URL
http://testphp.vulnweb.com/artists.php?artist=1
```
  













