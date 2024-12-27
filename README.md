# CODTECH_TASK2
## WEB APPLICATION PENETRATION TESTING
## Personal information 
- Name : Premkumar Soni
- Company : CODTECH IT SOLUTIONS PVT.LTD
- ID : CT08DBS
- Domain : Cyber Security & Ethical Hacking
- Duration: 20th Dec 2024 To 20th Jan 2025
- Mentor : Neela Santhosh kumar

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
- XSS vulnerabilities occur when an attacker is able to inject malicious scripts into web pages that other users view.
- These scripts can steal session cookies, deface websites, or redirect users to malicious sites.

- step 1 : Now first open the site and write xss payload on serachbar.
```payload
<script>alert("XSS vulnerability found")</script>
```
![image](https://github.com/user-attachments/assets/b622d740-4a3c-42c9-8654-8196b1e75555)

- step 2 : click on the go or tap ENTER. Now here you see we find XSS vulnerability in testphp.vulnweb.com site.

![image](https://github.com/user-attachments/assets/93508085-ec0d-480b-82e8-611469ed5891)

- More Payload :
<1>
  ```1.Payload
  <image/src/onerror=prompt(8)>
  ```

  ![image](https://github.com/user-attachments/assets/d29302ba-1dfe-45bc-a969-948fe7d0166f)

  ![image](https://github.com/user-attachments/assets/60d60c8c-7c71-4dc0-8887-3abf4c5e21fe)
<2>
 ```2.payload
<object src=1 href=1 onerror="javascript:alert(1)"></object>
```
![image](https://github.com/user-attachments/assets/9f525425-fc1d-43f1-8551-f593d82b6ce7)

![image](https://github.com/user-attachments/assets/ee5eeb4d-4711-4a0b-9c55-0c786c9e5ab4)


***2. SQL injection Vulnerability***

- SQL injection vulnerabilities allow attackers to manipulate SQL queries by injecting malicious input.
- This can lead to unauthorized access to the database, data leakage, or even data manipulation.

- Step 1 :  we identify the phpid of ***testphp.vulnweb.com*** site.

  ![image](https://github.com/user-attachments/assets/61e8736f-0775-411b-b199-ee06e6a0dc08)

- Step 2 : copy The given url.

```URL
http://testphp.vulnweb.com/artists.php?artist=1
```
- Step 3 : open the kali linux terminal.
- Now write the given command for perform SQL injection.
- here -u refers for URL & --dbs for database.

```URL
sqlmap -u http://testphp.vulnweb.com/artists.php?artist=1 --dbs
```
![image](https://github.com/user-attachments/assets/ac991ea7-e099-4417-9ea8-cc054b60b2bb)
![image](https://github.com/user-attachments/assets/1cc8b432-8ff6-4992-909b-89e7eaeec607)

- Now you see that we got a two databases. first is acuart and second is information_schema.
- Now we go to the inner in acuart database.

- Step 4 : Now follow this commnd for find columns in acuart database.
```COMMAND
sqlmap -u http://testphp.vulnweb.com/artists.php?artist=1 -D acuart --columns
```
![image](https://github.com/user-attachments/assets/d49730b3-fdac-422b-a83e-a10d4ca7e44d)
![image](https://github.com/user-attachments/assets/b27503b2-9ecb-436e-a738-c7f27ecce8b1)
![image](https://github.com/user-attachments/assets/642a7e93-afa0-42cf-afec-dca12106f875)

- Now you see we got columns of databases.

- step 5 : Retrieve data from the pass column using the following command.

```COMMAND
sqlmap -u http://testphp.vulnweb.com/artists.php?artist=1 -D acuart -C pass  --dump
```
![image](https://github.com/user-attachments/assets/0cea7771-9a3f-4ca4-959d-3b96360ebee3)
![image](https://github.com/user-attachments/assets/be536d09-1175-4123-bec8-a4b488436316)

- now you see we got the data from pass column.
- This is a SQL based vulnerability which we found in testphp.vulnweb.com.

***3. Insecurity authentication***
- Insecure authentication vulnerabilities arise when authentication mechanisms do not adequately protect user credentials.
#### i.unencrypted username and password
- Step 1: Visit testphp.vulnweb.com and go to the signup page. Enter your username and password, but do not click the login button yet. Open Wireshark and navigate to the currently connected network module. Now, click the login button on the web page.

![image](https://github.com/user-attachments/assets/7bdef671-45d3-4dca-8b79-c9ac864504e7)

- Step 2: Wireshark will start capturing packets.
  
![Screenshot 2024-12-25 113311](https://github.com/user-attachments/assets/0a3c8779-0056-4d03-8c24-9b690a0da78f)

- Step 3: In Wireshark, select the filter option and search for "http". You will see HTTP POST packets. Click on  Post packets.
  
![image](https://github.com/user-attachments/assets/19c5a1e3-725e-4f0b-86a6-4538db48c1fd)

- Step 4: Select the "HTML Form URL Encoded" option from the packet details pane. You'll notice that the username (uname) and password (pass) are sent in plaintext, without encryption.
  
![image](https://github.com/user-attachments/assets/f5795b99-e62d-44a3-9741-37db46ce4a82)

- Insecure Authentication: Transmitting credentials without encryption.
- Vulnerability: Lack of encryption exposes sensitive information.

## Conclusion
- Web Application Penetration Testing is essential for identifying and fixing security vulnerabilities in web applications. By conducting thorough tests and providing remediation recommendations, we can significantly improve the security of web applications and protect them from potential attacks.


  













