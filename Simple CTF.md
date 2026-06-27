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
















