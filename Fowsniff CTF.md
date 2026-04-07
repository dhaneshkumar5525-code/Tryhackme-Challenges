# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.

<img width="640" height="482" alt="image" src="https://github.com/user-attachments/assets/ccfe68fa-47c7-4d52-93cd-55a90eec442c" />

### This report details the methodology and steps taken to compromise the Fowsniff CTF machine on TryHackMe. The objective was to gain initial access, escalate privileges to root, and retrieve the user and root flags. This machine is perfect for beginners as it includes a guided methodology.
### Reconnaissance Phase:
### - Started with network scanning to gather initial information  
### - Used Nmap to identify open ports and services  

<img width="994" height="391" alt="image" src="https://github.com/user-attachments/assets/9aa34801-fc85-46ac-9826-b785f10751d1" />

### Open Ports Identified:
### - Discovered open ports during initial scan  
### - Port 22 → SSH service  
### - Port 80 → HTTP web service  
### - Port 110 → POP3 email service  
### - Port 143 → IMAP email service  

### HTTP Service Enumeration (Browser):
### - Accessed web service through browser using port 80  
### - Reviewed webpage content and structure  
### - Looked for visible links, forms, and inputs
<img width="1159" height="733" alt="image" src="https://github.com/user-attachments/assets/f8ae8cf8-6b88-4e29-8ce4-d714e1a1a389" />

### OSINT Findings
### - Identified a compromised Twitter handle leading to a Pastebin link for further investigation  
<img width="822" height="878" alt="image" src="https://github.com/user-attachments/assets/0088591e-1e0d-4e50-9c29-1e877c79a9d1" />

### - Located a Pastebin dump containing leaked passwords for analysis  
<img width="822" height="766" alt="image" src="https://github.com/user-attachments/assets/881fe47a-f33e-4fdd-bd4a-bee74c88d8ec" />

### - Used CrackStation tool to crack and retrieve plaintext passwords from hashes  
<img width="1909" height="644" alt="image" src="https://github.com/user-attachments/assets/bcde89cc-2ff9-403a-9c82-ea459bc7f405" />

### - Used Metasploit to test multiple usernames and passwords on POP3 to find valid login credentials  
### For the brute force I have created fowsniff_users and fowsniff_passwords
<img width="689" height="213" alt="image" src="https://github.com/user-attachments/assets/17fd553c-e135-40b4-8a9f-54ee39a8560a" />

<img width="556" height="246" alt="image" src="https://github.com/user-attachments/assets/a794bb4d-041e-4754-ae70-ccf79606061f" />

### - Used Metasploit auxiliary modules to search for valid POP3 login credentials  
<img width="1106" height="888" alt="image" src="https://github.com/user-attachments/assets/dd138e3e-8527-45a3-8097-74c26ee91e52" />

### After Selecting the Auxillary Moudule
### >Show options >Set Sucess on True >Set Users file >Set Password file >Enter exploit.
<img width="1919" height="734" alt="image" src="https://github.com/user-attachments/assets/ac2da91f-dbac-4fcb-8dc0-3136cba84ed3" />

### Found Username and The Password > Connecting using Netcat command:
### Netcat Overview
### - Netcat (nc) is a networking tool used for making connections and testing services  
### - Known as the “Swiss Army knife” of networking  
### - Used for port scanning and basic network communication  
### - Can act as both client and server for testing purposes  ### Netcat Overview
<img width="765" height="155" alt="image" src="https://github.com/user-attachments/assets/a9cd4c73-2393-4c0f-871b-ebbc7edb011d" />

### There are Two messages inside the seina user. Use command RETR 1 and 2 to retrive messages.
<img width="1297" height="647" alt="image" src="https://github.com/user-attachments/assets/94a06a65-cfd1-44f2-b07f-059dc57a133b" />

### In the Mail (Messages) We have Found the Temporary password of SSH.
<img width="1192" height="880" alt="image" src="https://github.com/user-attachments/assets/13c944d4-1d85-4e75-90cf-388f838c8689" />

### After retrieving the second message Baksteen was said to change the Temporary password.
<img width="1259" height="809" alt="image" src="https://github.com/user-attachments/assets/47bbdeb6-38a3-4b0e-8ab9-8cb8bebc3bab" />

### Now We will use User: Baksteen and Temporary Password to Login through SSH:
<img width="1506" height="620" alt="image" src="https://github.com/user-attachments/assets/b3fd02a0-7a9d-4b07-99ed-67d03bc27876" />

<img width="1260" height="622" alt="image" src="https://github.com/user-attachments/assets/2a1a5a03-7e99-4979-b68c-576de8276839" />

### After gaining access we enumerate the system, as user “baksteen” belongs to two different groups. We use to try to find files that belong to the “users” group and find a file called “cube.sh”.


### find / -group users -type f 2>/dev/null
<img width="1253" height="673" alt="image" src="https://github.com/user-attachments/assets/31bac4c8-a4dc-448b-a045-d8be36f45671" />

### We take a look at the content of the file and find it contains the message that comes once we login through SSH.

### cd /opt/cube
### cat cube.sh
### Now go to the Pentestmonkey and Copy the Python Reverse Shell code.
<img width="1408" height="955" alt="image" src="https://github.com/user-attachments/assets/db0aac30-a66e-4cee-9338-d4458bab4c52" />

### Enter the IP address and Port
<img width="1916" height="525" alt="image" src="https://github.com/user-attachments/assets/f247423f-cbc4-4cb2-9ac9-95ed2b4b4707" />

### Now Enter Bakstenn and Temporary Password to establish the connection.
<img width="737" height="126" alt="image" src="https://github.com/user-attachments/assets/9c6fc9d2-8598-42fd-a5f0-35d28ad6210e" />

### Now listen through lvnp 4444 > Ls there is flag.txt >Cat flag.txt
<img width="1341" height="980" alt="image" src="https://github.com/user-attachments/assets/cde91c90-7e94-4fe9-ab5a-0d2e48721a3a" />

<img width="1188" height="549" alt="image" src="https://github.com/user-attachments/assets/bc73bbcc-4c62-48f5-863b-e8b7e727c5e7" />

# Congratulations!!! We have Completed the Room.
<img width="1301" height="406" alt="image" src="https://github.com/user-attachments/assets/33a15390-7358-4d81-aab0-3ff0043f05db" />










