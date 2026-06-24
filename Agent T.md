# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1716" height="385" alt="image" src="https://github.com/user-attachments/assets/4c2f4c0b-4ab2-484f-972f-d774be2b59b1" />

### Agent T
### Something seems a little off with the server.
### Turn on the kali machine and connect with the opnvpn to tryhackme
<img width="875" height="254" alt="image" src="https://github.com/user-attachments/assets/4cceba3f-1171-467e-b103-9dcf5a82db11" />

### Start the target machine
<img width="1304" height="281" alt="image" src="https://github.com/user-attachments/assets/455d96cc-65f2-4de9-b9c2-9a6cc055d6ef" />

### Lets enumerate the target machine 10.48.172.246 using network scan 
### nmap -sV -sC 10.48.172.246 -Pn
<img width="997" height="387" alt="image" src="https://github.com/user-attachments/assets/03949066-ac07-4b8e-9521-36e71415b4c2" />

### Here we can see port 80 is open and lets open in browser
<img width="1920" height="1049" alt="image" src="https://github.com/user-attachments/assets/1f669b5a-5fa3-489e-b3bb-2003eb70dea1" />

### We can see the port 80 http is using PHP 8.1.0-dev
<img width="848" height="237" alt="image" src="https://github.com/user-attachments/assets/9b13035b-12f5-4bea-9615-2f9ba9400dd6" />

### Lets search for the php 8.1.0-dev vulnerability
<img width="1206" height="908" alt="image" src="https://github.com/user-attachments/assets/32d322fe-b260-4afc-984b-fe3b54ca48c5" />

### We can see the vulnerability has remote code execution which cause to open the back door
### Lets use the exploit from exploit database
<img width="1206" height="908" alt="image" src="https://github.com/user-attachments/assets/97866a51-83b8-4b6a-a956-17cd0a047e25" />

### Lets save the exploit. Enter the command
### nano php-8.1.0-exploit.py
<img width="1897" height="827" alt="image" src="https://github.com/user-attachments/assets/4d3cb5e4-55f6-4474-8449-c66fac489076" />

### Enter the host name 
<img width="1904" height="720" alt="image" src="https://github.com/user-attachments/assets/7e7e53e8-845b-49af-b2b2-c74e501ca84c" />

### Lets run the exploit. Enter the command 
### python php-8.1.0-exploit.py 
<img width="770" height="227" alt="image" src="https://github.com/user-attachments/assets/6cca6eb9-534e-46f4-a9a6-54c421cd5497" />

### Enter whoami to see the access 
<img width="1092" height="558" alt="image" src="https://github.com/user-attachments/assets/975cde7e-e36d-49da-9e8b-d760d6429ee1" />

### Lets try to find the flag, Enter the command 
### find / -type f -name "*.txt" 2>/dev/null
<img width="1307" height="558" alt="image" src="https://github.com/user-attachments/assets/18f48f6a-25f4-42b5-beb5-819005d5ed6d" />

### Enter the command : cat /flag.txt
<img width="818" height="97" alt="image" src="https://github.com/user-attachments/assets/8e20f567-4854-435e-ac31-c7d113a4e353" />

### flag{4127d0530abf16d6d23973e3df8dbecb}
### Answer
<img width="1280" height="158" alt="image" src="https://github.com/user-attachments/assets/d993c252-d5e2-4a90-bb39-8f66b34646f3" />

## Congratulations !!! We have Successfully Completed the Room
<img width="1461" height="322" alt="image" src="https://github.com/user-attachments/assets/8ad7de4f-a0d0-4b58-ab1c-2cba13be2ac0" />

### We are getting recognized
<img width="1920" height="542" alt="image" src="https://github.com/user-attachments/assets/178e109f-a045-4831-b7f0-2e6d66d99129" />






































