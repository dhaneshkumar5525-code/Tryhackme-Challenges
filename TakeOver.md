# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1534" height="333" alt="image" src="https://github.com/user-attachments/assets/cb7cc7ea-d7f8-4728-9bd8-d25a9a9a18f5" />

### TakeOver
### This challenge revolves around subdomain enumeration.
## Task 1 : Help us
### Problem
### Futurevera received a ransom threat from hackers claiming they could take over the company's infrastructure. Our goal is to identify the vulnerabilities that could allow such an attack.
### What We Have to Do
### • Enumerate the target website and its services.
### • Discover hidden resources and potential vulnerabilities.
### • Exploit identified weaknesses where applicable.
### • Assess the impact of a successful compromise.
### Solution
### Performed reconnaissance, enumerated the target, identified vulnerabilities, exploited the attack path, and determined what an attacker could potentially take over.

### Lets start the challenge turn on the target machine - 10.49.128.67
### Now we will perform nmap scan on the target machine
### nmap -sC -sV -p- 10.49.128.67 
<img width="1544" height="697" alt="image" src="https://github.com/user-attachments/assets/23e86cb8-8c01-4af2-8e75-943b897657be" />

### Port 22 80 and 443 is open 
### Hint: Don't forget to add the 10.49.128.67 in /etc/hosts for futurevera.thm ; )
### Lets enter this dns entry of url and ip address in the local system /etc/hosts
### sudo nano /etc/hosts
<img width="1339" height="308" alt="image" src="https://github.com/user-attachments/assets/7476cfa2-158d-4cc1-8b91-9ead3ea6f02f" />

### Lets try accessing the url futurevera.thm from the browser
<img width="1705" height="975" alt="image" src="https://github.com/user-attachments/assets/3e4e1ca0-7cec-45af-84cf-526d37a48d6d" />

### Click advance and accept the risk and continue
<img width="1920" height="949" alt="image" src="https://github.com/user-attachments/assets/e846b1f5-ee5a-4cfd-ac6d-558806b115b2" />

### Now we can see the page lets find the hidden directory using gobuster
<img width="1902" height="489" alt="image" src="https://github.com/user-attachments/assets/2690d379-7b88-46c1-b489-473d76709a44" />

### We can see error failed to verify the certificate 
### gobuster dir --help
<img width="1919" height="661" alt="image" src="https://github.com/user-attachments/assets/103674fc-5bf1-40f0-b0ec-0fa8ad45ff7f" />

### We can see add -K will skip the certificate. Lets try
<img width="1713" height="694" alt="image" src="https://github.com/user-attachments/assets/63ed1ee9-8111-4ee3-9beb-c315ddbe56a6" />

### We did not find any thing valuable for further investigation. 
### Lets use fuzz tool

























