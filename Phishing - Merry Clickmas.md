# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Phishing - Merry Clickmas
### Today We will learn how to use the Social-Engineer Toolkit to send phishing emails.
<img width="1899" height="420" alt="image" src="https://github.com/user-attachments/assets/70dbc476-9343-4589-8065-817b4b767444" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/114bbb79-2a65-4c31-bf0d-4df2b5f1b085" />

### We are joining TBFC’s authorized red team during scheduled penetration testing to evaluate the company’s security awareness
### The goal is to simulate phishing attacks to check whether employees can correctly identify and avoid malicious links
### We will work alongside the red team members (Recon McRed, Exploit McRed, and Pivot McRed) to plan and execute the phishing campaign
### This exercise will help determine if additional cybersecurity awareness training is needed

### Social Engineering
### We will understand that social engineering is the act of tricking people into making security mistakes like sharing passwords or opening malicious files
### Instead of attacking systems directly, attackers target humans by exploiting psychological factors like urgency, curiosity, and authority
### This is why social engineering is often called “human hacking,” since it relies on manipulating people rather than breaking technical systems
<img width="1012" height="595" alt="image" src="https://github.com/user-attachments/assets/a70c6693-3b94-493d-93e4-07dbefac1564" />

### Phishing
### We will understand that phishing is a type of social engineering attack that mainly uses messages like email, SMS, calls, QR codes, and social media to trick users
### The attacker’s goal is to make the user click, open, or reply so they can steal data, money, or system access
### These attacks are becoming harder to detect, so users are trained to STOP and think before taking any action on suspicious messages
### Suspicious?
### Telling me to click something?
### Offering me an amazing deal?
### Pushing me to do something now?
### The second S.T.O.P. reminds users to follow the following instructions:

### Slow down. Scammers run on your adrenaline.
### Type the address yourself. Don’t use the message’s link.
### Open nothing unexpected. Verify first.
### Prove the sender. Check the real From address/number, not just the display name.

### Delivery via Social-Engineer Toolkit (SET)
<img width="750" height="393" alt="image" src="https://github.com/user-attachments/assets/1c80f89e-157a-4eb2-a1d4-2e9d58384066" />

### Once the phishing page is prepared, the next step is delivering it to the target in a convincing way
### In real phishing scenarios, attackers avoid using personal emails and instead impersonate trusted or familiar senders to increase credibility
### The effectiveness of a phishing email depends heavily on how realistic and trustworthy it appears to the target user
### To simulate this process, we use the Social-Engineer Toolkit (SET), an open-source framework designed for social engineering and phishing simulations
### We will now follow the SET workflow step by step to configure and generate the phishing email for the target user

### We will launch the tool by running `setoolkit`, which opens an interactive menu-driven interface
### From the main menu, we will select option 1 for Social-Engineering Attacks, which contains different phishing-related attack modules

### Lets start the attack box and enter setoolkit in terminal
<img width="1024" height="509" alt="image" src="https://github.com/user-attachments/assets/6ca7a6d5-fb55-4c10-9fa1-4f07050bf82b" />

### We can see the Interface
<img width="1018" height="583" alt="image" src="https://github.com/user-attachments/assets/21d749ff-d3bc-43e7-a1a0-29d9dc2d0932" />

### After choosing Social-Engineering Attacks, we will see another menu listing different attack options
### We will select option 5, which corresponds to the Mass Mailer Attack
<img width="1021" height="407" alt="image" src="https://github.com/user-attachments/assets/a73a2c34-0388-4cda-aaec-0e0dfdd07b84" />

### We will choose between sending a phishing email to a single target or to multiple recipients
### In this case, we will select option 1, which is the E-Mail Attack targeting a single email address
<img width="997" height="247" alt="image" src="https://github.com/user-attachments/assets/ff71c568-0b58-40f2-afe4-1d819ddac8d4" />

### We will now go through a series of prompts to configure how the phishing email is sent, pressing Enter after each input
### Send email to: We will target `factory@wareville.thm`
### Delivery method: We will choose `Use your own server or open relay`
### From address: We will spoof `updates@flyingdeer.thm`, a trusted shipping contact
### From name: We will set the sender name as `Flying Deer`
<img width="1006" height="244" alt="image" src="https://github.com/user-attachments/assets/7d2d4044-72ad-4fc4-b7a7-dabf01f6aee4" />

### Username for open-relay: We will leave this blank and press Enter
### Password for open-relay: We will leave this blank and press Enter
### SMTP server address: We will send directly via the TBFC mail server using `MACHINE_IP`
### SMTP port: We will keep the default port `25` and press Enter
<img width="706" height="111" alt="image" src="https://github.com/user-attachments/assets/ee4ab0c5-bf29-4361-bb41-07e0f5fea526" />

### Flag this message as high priority: We will choose `no`, since it is not required for this simulation
### Attach a file: We will select `n`, as we are not sending any attachments
### Attach an inline file: We will also select `n`, keeping the email simple and focused on the link-based trap
###  Please confirm the new schedule by visiting http://CONNECTION_IP:8000 --- http://10.81.191.86:8000
<img width="704" height="198" alt="image" src="https://github.com/user-attachments/assets/e8da4feb-59f8-4367-907b-3a1e83a2358f" />

### After sending the phishing email, I monitored the server.py terminal for captured credentials. 
<img width="717" height="176" alt="image" src="https://github.com/user-attachments/assets/8ef57733-04eb-4b84-b6cd-e4d5972c1deb" />

### Within 1-2 minutes, the TBFC employee fell victim to the attack.
<img width="723" height="478" alt="image" src="https://github.com/user-attachments/assets/dbc33384-35e6-41b0-8a44-9c3ef25116f8" />

### We have successfully captured the credentials as part of the phishing simulation
### What is the password used to access the TBFC portal?
### unranked-wisdom-anthem
### Browse to http://10.81.191.86 from within the AttackBox and try to access the mailbox of the factory user 
### to see if the previously harvested admin password has been reused on the email portal. What is the total number of toys expected for delivery?
<img width="1385" height="663" alt="image" src="https://github.com/user-attachments/assets/f32e0a06-f164-4bdd-941e-b3c186feddfe" />

### We have successfully logged in. We can there are two mails in the inbox
<img width="1418" height="726" alt="image" src="https://github.com/user-attachments/assets/9b2fc945-227d-4a3c-a062-786068a61d7d" />

### Opening the first mail, Subject-shipping schedule change 
<img width="1355" height="540" alt="image" src="https://github.com/user-attachments/assets/f490aa22-33d1-4cce-9cc8-09a62ddd438e" />

### Opening the second mail, Subject- Urgent: Production & Shipping Request - 1984000
<img width="1434" height="728" alt="image" src="https://github.com/user-attachments/assets/ea186363-dd23-4fb0-9e9e-c0b5579852db" />

### try to access the mailbox of the factory user to see if the previously harvested admin password has been reused on the email portal. 
### What is the total number of toys expected for delivery?
###  1984000 Units

### Attack Chain Summary

### Reconnaissance:  We identified a trusted partner (Flying Deer) to make the phishing email more believable
### Infrastructure:  We deployed a credential harvesting page running on port 8000
### Weaponization:   We crafted a convincing phishing email using SET
### Delivery:        We sent the email by spoofing a trusted sender via SMTP
### Exploitation:    The target user submitted their credentials on the fake login page
### Actions Impact:  We used the captured credentials to access the email system through credential reuse
<img width="1624" height="510" alt="image" src="https://github.com/user-attachments/assets/fc494dd0-d658-422b-8394-f81ec600c23f" />

## Congratulations !!! We have Successfully Completed the Room
<img width="1902" height="548" alt="image" src="https://github.com/user-attachments/assets/046eba01-9d8e-4f66-bdb9-e5e5c4151e7a" />









