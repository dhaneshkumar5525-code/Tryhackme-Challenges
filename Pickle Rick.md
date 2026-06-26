# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="720" height="113" alt="image" src="https://github.com/user-attachments/assets/02bc5ea7-a45c-4bed-a164-b1c04a2542be" />

### Pickle Rick
### A Rick and Morty CTF. Help turn Rick back into a human!
### • Enumerate the web application to identify exposed files and services.
### • Exploit discovered vulnerabilities to gain access to restricted areas.
<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/2fd87e3e-f4ba-46f5-8838-1276791fef61" />

### Turn on the target machine - 10.49.175.14 
### Lets perform the nmap scan and save the file as scan2.txt. Enter the command 
### nmap -sC -sV -oN scan2.txt 10.49.175.14 
<img width="1293" height="478" alt="image" src="https://github.com/user-attachments/assets/e8a4cc1f-8a10-4759-a8ef-5c74cc517b1d" />

### We can see port 22 and 80 is open. Lets access the port 80 from the browser
<img width="1920" height="685" alt="image" src="https://github.com/user-attachments/assets/7da73c71-5732-4500-9742-1c659e0007dc" />

### Rick has turned himself into a pickle and forgotten the password to his computer. Your goal is to help him regain access and find the missing ingredients for his potion.

### • Enumerate the target to discover services and hidden files.
### • Find or bypass the password to access Rick's computer.
### • Search the system for the three secret ingredients.
### • Escalate privileges if needed to access protected files.
### • Collect all three ingredients to complete the challenge.

### Lets view the source code and see what we can find. Add view-source in the url
<img width="1364" height="684" alt="image" src="https://github.com/user-attachments/assets/cd97de84-5285-4138-811f-a96c6468b1e9" />

### Nice, We can see Username: R1ckRul3s in the code, since we know the ssh is open lets find the password 
### Lets enumurate the website using gobuster to find the hidden directories
### gobuster dir -u http://10.49.175.14 -w /usr/share/dirb/wordlists/common.txt
<img width="1568" height="771" alt="image" src="https://github.com/user-attachments/assets/3ccefff3-240f-43ac-bd70-c1d7aa5e44b9" />

### We found interesting stuff /assets amd robot.txt and lets navigate to the /assets page
<img width="1197" height="489" alt="image" src="https://github.com/user-attachments/assets/27e07c13-8793-43dc-9e15-5b0a3d519ddc" />

### We have found multiple files lets open one by one
### fail.gif
<img width="452" height="304" alt="image" src="https://github.com/user-attachments/assets/127a9777-36ab-4667-9cd2-8550b96659c6" />

### Picklerick.gif 
<img width="722" height="396" alt="image" src="https://github.com/user-attachments/assets/ceff1cf0-9eb5-4c8d-8804-93c9ad1322f5" />

### Portal.gif
<img width="700" height="579" alt="image" src="https://github.com/user-attachments/assets/f27aa101-7a26-4ca9-801d-e26b65383d99" />

### rickandmonty.jpeg
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/9b8ebd71-6962-4cf5-8b1e-690b1ddb7d2d" />

### Lets navigate to the /robot.txt file which we found in the gobuster enumeration
<img width="1587" height="166" alt="image" src="https://github.com/user-attachments/assets/91aafc07-bdec-47c3-8942-1a2f5f7b7fb5" />

### We found a text may be the password lets see a login page available
### login.php is available enter username and the password we found
<img width="1695" height="593" alt="image" src="https://github.com/user-attachments/assets/2bb9333e-689d-4d7d-8e7a-f0db72a1d269" />

### Click enter 
<img width="1731" height="323" alt="image" src="https://github.com/user-attachments/assets/2b87e935-90b1-49dc-970c-6d6b8fbc7555" />

### Target machine time is over. Lets start the target machine - 10.49.176.12
<img width="1301" height="276" alt="image" src="https://github.com/user-attachments/assets/a621bd3c-e6fb-4a67-b25a-de122208018a" />

### Enter ls command 
<img width="1693" height="535" alt="image" src="https://github.com/user-attachments/assets/29fe3563-567e-40a4-92af-d955438e8bd7" />

### cat Sup3rS3cretPickl3Ingred.txt
<img width="1695" height="525" alt="image" src="https://github.com/user-attachments/assets/b3379599-3e29-44cb-8b0f-ac21df9d14a1" />

### Command disabled. we cannot use the cat to read the file 
### Since cat command is disabled lets use sudo less command
### sudo less Sup3rS3cretPickl3Ingred.txt
<img width="1688" height="401" alt="image" src="https://github.com/user-attachments/assets/fd5c9557-0a86-43d3-bca5-317fea56770d" />

### mr. meeseek hair

### For second ingredients lets check all the files
<img width="1694" height="424" alt="image" src="https://github.com/user-attachments/assets/6b079ccf-a42e-4f08-9283-8ce2394773dd" />

### We can see the second ingredients
<img width="681" height="155" alt="image" src="https://github.com/user-attachments/assets/73ed73a0-a482-4bb3-acc2-c0b3fd7aaeb4" />

### Since we cannot open the file lets try copying the file into the main directory
### Enter the command 
### sudo cp /home/rick/second\ ingredients ./ingred2.txt
<img width="922" height="330" alt="image" src="https://github.com/user-attachments/assets/c3687ab5-b652-498a-9f5b-6b2d377ac664" />

### We copied file will be in the present working directory - ingred2.txt
<img width="1453" height="542" alt="image" src="https://github.com/user-attachments/assets/548a4742-13aa-4914-981e-cff4ba3b3957" />

### Enter in the url - ingred2.txt
<img width="1408" height="153" alt="image" src="https://github.com/user-attachments/assets/2f0172fa-591c-49db-8a03-f5dc1ecc1c5e" />

### Jerry tear
### Lets find the 3rd ingredient and copy to the pwd
### Enter the command
### sudo cp /root/3rd.txt ./third.txt
<img width="1441" height="310" alt="image" src="https://github.com/user-attachments/assets/e48c6ffb-1711-4dc3-bbca-249fbcb9b2ac" />

### We can see the third.txt
<img width="1695" height="558" alt="image" src="https://github.com/user-attachments/assets/ce483e81-2eb9-4f8f-9eba-ffce598a127f" />

### We found the third ingrediant
<img width="1266" height="188" alt="image" src="https://github.com/user-attachments/assets/701dcdc8-f1e5-4223-9b9b-af0260bc177d" />

### fleeb juice
<img width="1289" height="219" alt="image" src="https://github.com/user-attachments/assets/f607658d-420c-4ba8-a9e1-1f4c57a464ae" />

<img width="640" height="357" alt="image" src="https://github.com/user-attachments/assets/242b7e17-e203-4933-9f0b-994fe41993d5" />


### Finally we have all our secret ingredients. We work out the potion and finally transform Rick back to a human from a pickle !
<img width="617" height="356" alt="image" src="https://github.com/user-attachments/assets/dcb2acc4-fda7-4fad-8201-6253cb81e467" />


## Congratulations !!! We have Successfully Completed the Room.
<img width="1595" height="204" alt="image" src="https://github.com/user-attachments/assets/3f38d286-6e6e-4aed-a5f1-1c83fd0e331a" />




