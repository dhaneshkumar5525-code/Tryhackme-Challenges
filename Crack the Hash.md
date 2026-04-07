# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="474" height="292" alt="image" src="https://github.com/user-attachments/assets/9e6a8094-4761-4213-99ef-366fc5d60490" />

### Crack the Hash Overview
### - Walkthrough focuses on cracking password hashes in TryHackMe  
### - Identified hash types before attempting to crack them  
### - Applied techniques to convert hashes into readable passwords  
<img width="1902" height="473" alt="image" src="https://github.com/user-attachments/assets/dbe18a80-3fde-4c39-86e3-77c87ad49845" />

### Hash Cracking Resources
### - Used online tools: https://hashes.com/en/decrypt/hash and https://crackstation.net/  
### - Used Kali Linux tools: Hash-Identifier and Hashcat for identifying and cracking hashes  
## Task:
### 1) Started hash cracking walkthrough with given hash: 48bb6e862e54f2a795ffc4e541caed4d  
### - First step is to identify the hash type before cracking 
<img width="1714" height="703" alt="image" src="https://github.com/user-attachments/assets/d3e4536d-43bf-47d7-9d4b-530d08a59a1c" />

### 2) Analyzed the given hash: CBFDAC6008F9CAB4083784CBD1874F76618D2A97  
### - Identified hash type before attempting to crack it  
<img width="1719" height="651" alt="image" src="https://github.com/user-attachments/assets/6ff15855-c2e0-4cda-8e93-bd212d048104" />

### Now We will use kali Linux to Crack the Hash and Compare both kali and Online Crack Station:
<img width="1109" height="660" alt="image" src="https://github.com/user-attachments/assets/bc07575e-9d1f-4ed5-8117-fab02eb46e2b" />

### These are the Possible Hash Types:
<img width="1169" height="471" alt="image" src="https://github.com/user-attachments/assets/cd37f7dc-4478-43f7-bf10-3029e593357f" />

### Now We will use hashid to know the mode number of the hash 
<img width="1189" height="331" alt="image" src="https://github.com/user-attachments/assets/461835a5-d504-4a39-9e84-bcf54ecaa716" />

### Now We will use the Hashcat -m (mode number) and the Hash /usr/share/wordlists/rockyou.txt
<img width="1175" height="97" alt="image" src="https://github.com/user-attachments/assets/658011a8-5f2b-4471-a383-37c504f94bad" />

### Hashcat Working
### - Takes a password guess from a wordlist  
### - Converts the guess into a hash using the same algorithm  
### - Compares generated hash with target hash  
### - If both match, the correct password is found  
<img width="1179" height="571" alt="image" src="https://github.com/user-attachments/assets/b293052e-d922-4017-b004-5f5d05558b40" />

### The Online Cracked password and Hashcat Password maches -password123

### 3) Analyzed the given hash: 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032  
### - Identified hash type before attempting to crack it  
<img width="1712" height="639" alt="image" src="https://github.com/user-attachments/assets/ca45f02f-1a92-499b-806c-0928e5ae28cf" />

### 4) Analyzed the given hash: $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom  
### - $ Possible sensitive hash value detected
### As you can see the hash was not found in Crack Station 
<img width="1717" height="703" alt="image" src="https://github.com/user-attachments/assets/9eef2abc-aaff-4c0c-a054-6521d439b354" />

### I have used Hashes.com to decrypt:
<img width="1671" height="830" alt="image" src="https://github.com/user-attachments/assets/bc7111d9-b3aa-41f0-a746-a1e567ebc470" />

### As you can see the decrypted hash is "bleh"
### 5) 279412f945939ba78ce0758d3fd83daa
<img width="1100" height="357" alt="image" src="https://github.com/user-attachments/assets/1506494d-f292-4fc2-a27e-b8da2cb9009a" />

## Task 1: Completed 
<img width="1576" height="656" alt="image" src="https://github.com/user-attachments/assets/a230347e-9c3a-4506-a341-7d969e6f3e87" />

### Task 2:
### Hash Cracking Task
### 1) Analyzed the given hash: F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85  
<img width="1716" height="649" alt="image" src="https://github.com/user-attachments/assets/5f4e765c-0a84-4e2a-a137-32bfa51d1c87" />

### 2) Analyzed the given hash: 1DFECA0C002AE40B8619ECF94819CC1B
<img width="1700" height="777" alt="image" src="https://github.com/user-attachments/assets/6dba08c5-c806-40b9-bc25-182806aa875a" />

### 3) Analyzed the given hash: $6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.  
### - Identified the use of salt: aReallyHardSalt  
### - Included salt in cracking process for accurate results
<img width="1705" height="774" alt="image" src="https://github.com/user-attachments/assets/e3b1fc76-6075-4fbd-be4c-0a38c15c0945" />

### 4) Analyzed the given hash: e5d8870e5bdd26602cab8dbe07a942c8669e56d6  
<img width="1701" height="715" alt="image" src="https://github.com/user-attachments/assets/eb53d55a-e0c7-4063-8d76-670efc07c06e" />

<img width="1627" height="860" alt="image" src="https://github.com/user-attachments/assets/5219cf7f-0483-45cd-afd9-0beb338f7771" />

### We have Completed the Room!!!
<img width="1182" height="362" alt="image" src="https://github.com/user-attachments/assets/5ea99ad5-5844-4e0b-a999-25067ff68a62" />




