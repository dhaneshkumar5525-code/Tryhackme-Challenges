# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations
### Passwords - A Cracking Christmas
### Today, We are Learn how to crack password-based encrypted files.
<img width="1900" height="422" alt="image" src="https://github.com/user-attachments/assets/d5aa06b5-f216-4e37-bc13-9e35803beeb3" />

## Task 1 Introduction
### Unusual encrypted files appear within The Best Festival Company’s systems, possibly containing sensitive North Pole data tied to Santa’s gift registry.  
### Sir Carrotbane begins cracking the files, highlighting how weak passwords can expose critical secrets and threaten festive balance.  
### • System instability revealed hidden encrypted PDF and ZIP files labeled “North Pole Asset List.”  
### • Files may contain parts of Santa’s master gift registry, valuable to Malhare.  
### • Task focuses on cracking encryption and identifying weak password vulnerabilities.  
### • Weak passwords risk exposing sensitive data, prompting urgency for the Elves to secure it.

### Learning Objectives  
### How password-based encryption protects files such as PDFs and ZIP archives.  
### Why weak passwords make encrypted files vulnerable.  
### • How attackers use dictionary and brute-force attacks to recover passwords.  
### • A hands-on exercise: cracking the password of an encrypted file to reveal its contents.  
### • The importance of using strong, complex passwords to defend against these attacks.

### The strength of protection depends almost entirely on the password. Short or common passwords can be guessed; long, random passwords are far harder to break.  
### Different file formats use different algorithms and key derivation methods. For example, PDF encryption and ZIP encryption differ in details (key derivation, salt use, hash iterations), affecting cracking difficulty.  

## Task 2 Attacks Against Encrypted Files
### How Attackers Recover Weak Passwords  

### Attackers usually avoid directly breaking encryption because modern cryptography is very strong, instead focusing on recovering the password that protects the file.  
### This is done by testing many possible passwords using automated methods until the correct one is found.
### • The most common methods are dictionary attacks, which try known or common passwords, and brute-force (or mask) attacks, which try all possible combinations.  

### Dictionary Attacks  
<img width="400" height="240" alt="image" src="https://github.com/user-attachments/assets/df12cdbe-e514-44f2-a3cf-b9d9ec825483" />

### “Disclaimer: “No passwords were guessed in the making of this joke.”

<img width="800" height="401" alt="image" src="https://github.com/user-attachments/assets/0552ad0c-b85d-405f-97c0-423ea4f4690b" />


### In a dictionary attack, attackers use a predefined list of potential passwords (a wordlist) and systematically try each one until the correct password is found.  
### These wordlists often include leaked passwords, common choices like "password123", and predictable patterns such as names, dates, and simple substitutions.
### • Dictionary attacks are effective because many users choose weak or commonly used passwords.  
### • They are usually faster than brute-force attacks since they test likely passwords first.  
### • Success depends heavily on the quality and relevance of the wordlist used.

### Mask Attacks  
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/abd2662d-c1a3-4b4a-b80b-9a6badc8948e" />

### Brute-force attacks try every possible combination of characters until the correct password is found, guaranteeing success but taking exponentially longer as password length and complexity increase.  
### Mask attacks improve efficiency by narrowing guesses to a known pattern, such as specific character types or formats like letters followed by numbers.
### • Brute-force attacks are exhaustive but slow, especially for long or complex passwords.  
### • Mask attacks reduce the search space by focusing on expected password structures.  
### • These methods are effective when attackers have partial knowledge of how a password may be formed.

### Practical Password Cracking Techniques (Attackers & Defenders Should Know)  

### • Attackers often start with wordlists like rockyou.txt or other common-password lists to quickly find weak passwords.  
### • If that fails, they switch to targeted wordlists based on the victim’s context, such as company or project names.  
### • Mask or incremental attacks are used next, testing structured patterns like letters followed by numbers for short passwords.  
### • GPU acceleration is used to speed up cracking significantly, especially for supported hashing algorithms.  
### • High CPU/GPU usage during cracking can be a detection signal on monitored systems, helping defenders spot attacks.

## Exercise
### Turn on the Target Machine
<img width="1466" height="387" alt="image" src="https://github.com/user-attachments/assets/a0802f09-8990-4da0-8d2c-d5aec0b9cae8" />

### Confirm the File Type
### Use the file command or open the file with a hex viewer. This helps pick the right tool.
### We can see the files on the Desktop
<img width="1568" height="757" alt="image" src="https://github.com/user-attachments/assets/c5277d3c-5f37-4ae3-bbae-755d8edf6003" />

### Tools to Use (Based on File Type)  

### • PDF: pdfcrack, john (pdf2john)  
### • ZIP: fcrackzip, john (zip2john)  
### • General: john (flexible), hashcat (GPU, faster)  
### • Pick tools based on file type and performance needs

### Try a Dictionary Attack First (fast, often successful)
### Example: PDF with pdfcrack and rockyou.txt:
### Command : pdfcrack -f flag.pdf -w /usr/share/wordlists/rockyou.txt 
### -f is file and -w is wordlists
<img width="1513" height="778" alt="image" src="https://github.com/user-attachments/assets/9d88a0f5-599e-4ab2-ac0e-d23b79e5754d" />

### We have cracked the file password "naughty list"
### Now unlock the password using the file
<img width="1017" height="488" alt="image" src="https://github.com/user-attachments/assets/83206eb6-c632-4477-96a7-0e5a394d3bfb" />

### We have captured the flag inside the file "THM{Cr4ck1ng_PDFs_1s_34$y}"
<img width="1558" height="582" alt="image" src="https://github.com/user-attachments/assets/ef4720c7-5850-4ba5-9c3b-6bab3de23d65" />

### Now for the Zip File:
### John can’t directly crack ZIP archives, so the file must be converted first.  
### Extract the hash into a compatible format that John can process.

### • zip2john → extract hash from ZIP  
### • Save hash to file  
### • Run john on extracted hash  
### • Enables ZIP password cracking via John

<img width="1127" height="154" alt="image" src="https://github.com/user-attachments/assets/9269af7a-0f3d-4483-b1fb-b84ed1ffe1a7" />

### Now We can see new file is added in desktop
<img width="1661" height="629" alt="image" src="https://github.com/user-attachments/assets/57625092-42fb-4a26-9482-3c50df452470" />


### Now use the new file ziphash.txt with the command
### john --wordlist=/usr/share/wordlists/rockyou.txt ziphash.txt
<img width="1336" height="428" alt="image" src="https://github.com/user-attachments/assets/e1ea1eec-1798-48a5-ac92-25683225dc54" />

### We found the password of the zip file "winter4ever"
<img width="1336" height="428" alt="image" src="https://github.com/user-attachments/assets/46d076a1-4562-45fa-a9f9-b9dfa010f06d" />

### Enter the password of the zip file
<img width="743" height="596" alt="image" src="https://github.com/user-attachments/assets/2c6be243-8052-4263-b2e9-8e243b894683" />

### We have captured the flag "THM{Cr4ck1n6_z1p$_1s_34$yyyy}"
<img width="810" height="624" alt="image" src="https://github.com/user-attachments/assets/f7dbe33c-1337-430b-99d3-82da5ce8a072" />

### Detection of Indicators and Telemetry  

### Offline cracking avoids login systems, so we must detect it on endpoints or jump boxes instead.  
### Monitoring focuses on process activity, known tools, and system behavior to reveal cracking attempts.

### • Watch for known binaries: john, hashcat, fcrackzip, pdfcrack, zip2john, pdf2john.pl, 7z, qpdf, unzip, perl  
### • Look for command-line patterns: --wordlist, --rules, --mask, -a 3, references to rockyou.txt or SecLists  
### • Monitor files like potfiles and session states: john.pot, hashcat.potfile, john.rec  
### • Track high CPU/GPU usage and related file/network activity  

### GPU and Resource Artefacts  

### GPU cracking causes high system usage and is easily noticeable on monitored systems.  
### Network activity may occur when downloading tools or wordlists before cracking begins.
### • High GPU usage, power draw, fan spikes (nvidia-smi → john/hashcat)  
### • GPU libraries: nvcuda.dll, OpenCL.dll, libcuda.so  
### • Downloads: rockyou.txt, wordlist repos  

### Here is the Final answers of the path
<img width="1618" height="619" alt="image" src="https://github.com/user-attachments/assets/fed1ea16-7dd4-4676-bfbc-9c505d0718d2" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1906" height="432" alt="image" src="https://github.com/user-attachments/assets/68c0bb94-dcbe-4a10-88f6-b4fbed9b356a" />









