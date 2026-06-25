# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1648" height="329" alt="image" src="https://github.com/user-attachments/assets/3898fcf8-a831-47e2-9944-8b3d7b98d31a" />

### MD2PDF
### TopTierConversions LTD is proud to present its latest product launch.
### Turn on the target machine - 10.49.172.49
<img width="1322" height="281" alt="image" src="https://github.com/user-attachments/assets/cd4aa71a-03f0-49c2-9fc2-be86ee8b0e76" />

### Now we are going to test this new product and lets start reconnaisance
### Lets perform nmap scan - nmap -sC -sV -Pn 10.49.172.49
<img width="1917" height="471" alt="image" src="https://github.com/user-attachments/assets/a09917d1-e6a8-443a-8150-f310f06af0c0" />

### We can see port 80 and 22 is open. Lets view the web page 
<img width="1916" height="581" alt="image" src="https://github.com/user-attachments/assets/060fa70f-b15b-4f73-9e54-6e15778df529" />

### This site MD2PDF stands Markdown2Pdf. This site converts html markdown into the pdf format
### Lets enumarate the website using gobuster
### Command:  gobuster dir -u  http://10.49.172.49/ --wordlist /usr/share/dirb/wordlists/common.txt
<img width="1315" height="534" alt="image" src="https://github.com/user-attachments/assets/e79aa53a-e481-4afb-b0f5-f54df8cbdd7c" />

### Lets navigate to the /admin directory
<img width="1690" height="211" alt="image" src="https://github.com/user-attachments/assets/2de5c0e0-e6c5-4172-bbd7-2f37c4517cc8" />

### That’s our first big clue. There’s something behind /admin, but only if the request comes from localhost. Smells like an SSRF opportunity.
### Lets see the source code
<img width="1720" height="165" alt="image" src="https://github.com/user-attachments/assets/888b5179-86d8-4700-933f-80775ffe1463" />

### Markdown + HTML = Weapon
### At first glance, the Markdown parser seems limited… until we test raw HTML
### Lets craft iframe and paste in the converter
### <iframe src="http://localhost:5000/admin"></iframe>
<img width="1738" height="603" alt="image" src="https://github.com/user-attachments/assets/a9971b2e-2feb-4919-9a94-b8f861c7f77b" />

### Click convert into the pdf
<img width="1920" height="431" alt="image" src="https://github.com/user-attachments/assets/63cca397-5d6f-4aae-8c16-43ad8b21ee98" />

### We found the flag: flag{1f4a2b6ffeaf4707c43885d704eaee4b}

## Congratulations !!! We have Successfully Completed the Room.
<img width="1628" height="329" alt="image" src="https://github.com/user-attachments/assets/d4a5311d-a609-4b74-82bd-02a0059d260d" />













