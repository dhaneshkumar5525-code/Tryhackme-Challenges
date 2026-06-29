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
### Lets use fuzz tool enter the commmand 
### ffuf -H "Host: FUZZ.futurevera.thm" -u https://10.49.172.64 -w /usr/share/dirb/wordlists/common.txt -fs 4605
### Virtual Host Enumeration with FFUF

### The following command fuzzes the **Host** header to discover hidden virtual hosts configured on the target web server.
### • `ffuf` – Launches the **Fuzz Faster U Fool** tool.
### • `-H "Host: FUZZ.futurevera.thm"` – Replaces `FUZZ` with words from the wordlist to discover virtual hosts.
### • `-u https://10.49.172.64` – Specifies the target web server.
### • `-w /usr/share/dirb/wordlists/common.txt` – Uses a wordlist of potential virtual host names.
### • `-fs 4605` – Filters responses of **4605 bytes** to hide the default page and display only valid results.

<img width="1542" height="815" alt="image" src="https://github.com/user-attachments/assets/080185a6-2b0c-4ab6-baff-39b5ecc8389a" />

### We can see the blog and support lets add them in the local dns /etc/hosts
### Sudo nano /etc/hosts and add blog and the support 
<img width="1336" height="413" alt="image" src="https://github.com/user-attachments/assets/2abd0ad4-175d-494e-9009-692826145fe1" />

### Lets try to access blog.futurevera.thm 
<img width="1920" height="975" alt="image" src="https://github.com/user-attachments/assets/168f3b50-9411-46b1-87ac-a347f0fcecb4" />

### Accept risk and contine
<img width="1915" height="1000" alt="image" src="https://github.com/user-attachments/assets/26f8642b-e5eb-47a5-b9c9-6b9784215649" />

### We can see the home page of the blog and lets explore about and post
<img width="1509" height="999" alt="image" src="https://github.com/user-attachments/assets/939d906f-58bc-48cd-bcd1-00d6434e70ce" />

### Post sections
<img width="1503" height="999" alt="image" src="https://github.com/user-attachments/assets/dfd1e57f-6871-4ef8-ae89-d70cfd5fffd6" />

### lets scroll down the page
<img width="1452" height="997" alt="image" src="https://github.com/user-attachments/assets/ed6ee4e3-9ace-4ff4-9338-991a5723aad5" />

### We didnot find anything valueable worth investigating. Lets explore the support.futurevera.thm
<img width="1487" height="980" alt="image" src="https://github.com/user-attachments/assets/3a1486ef-a55f-4bc4-bbc7-7ba8044b065d" />

### Click accept risk and continue
<img width="1561" height="1001" alt="image" src="https://github.com/user-attachments/assets/3d4f4694-866a-45ba-b7a3-3f107772af23" />

### Lets inspect the certificate
<img width="1532" height="975" alt="image" src="https://github.com/user-attachments/assets/e22bfb62-a08a-44bc-9c26-bd184a1b6a28" />

### Yay we have found subject alternative name : secrethelpdesk934752.support.futurevera.thm
### A company register all the san numbers with one certificate with the certificate authority in this was there will be no problem in renewing the expired liciences.

### Lets add the new url to the ip address in the /etc/hosts
<img width="1653" height="448" alt="image" src="https://github.com/user-attachments/assets/bbfe3405-0877-416d-8a83-0e918c09fffb" />

### Lets enter the new url in the browser
<img width="1511" height="874" alt="image" src="https://github.com/user-attachments/assets/2713c652-68c0-4882-9810-18b0db95fa72" />

###  It says - Hmm. We’re having trouble finding that site but if we look closely we have a flag
<img width="847" height="362" alt="image" src="https://github.com/user-attachments/assets/e3c14499-105b-4f32-b19b-bcc57ff23fac" />

### We have found the flag : flag{beea0d6edfcee06a59b83fb50ae81b2f}
### Lets enter it in the answer box
<img width="1295" height="171" alt="image" src="https://github.com/user-attachments/assets/d9f7d42e-6497-43ab-bc71-9b9c7e96f306" />

## Congratulations !!! We have Successfully Completed the Room.
<img width="1614" height="326" alt="image" src="https://github.com/user-attachments/assets/145d378e-0d2b-4010-9e67-35dd7b402770" />

  














