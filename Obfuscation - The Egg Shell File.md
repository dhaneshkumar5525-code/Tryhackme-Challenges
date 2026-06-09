# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Obfuscation - The Egg Shell File
### McSkidy keeps her focus on a particular alert that caught her interest: an email posing as northpole-hr.
<img width="1711" height="426" alt="image" src="https://github.com/user-attachments/assets/7c85db46-53a7-44c5-94c0-64c70fe71b31" />

## Task 1 Introduction
### We are going to investigate a suspicious phishing email and PowerShell file, as the downloaded file contains hidden and unreadable code that may be malicious.  
### We will learn how attackers use obfuscation to hide code and how we can analyze and decode it accordingly.  

### • WareVille systems are experiencing unusual activity and security alerts  
### • A suspicious email claimed to be from northpole-hr, which does not exist  
### • The email led to the download of a small PowerShell file  
### • The file contains random-looking strings that are not readable at first glance  

## Task 2 Obfuscation & Deobfuscation
### What is obfuscation? Obfuscation is the practice of making data difficult to read and analyze so attackers can avoid detection and slow down investigations.  
### How do attackers hide suspicious content? They use techniques like ROT1, which shifts each letter forward by one position in the alphabet to disguise words accordingly.  
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/35372c21-9a56-4b9b-b0f2-04f30e00fb7c" />

### • Attackers use obfuscation to evade security tools and analysts  
### • Security solutions may block files containing specific keywords  
### • ROT1 is a simple cipher that shifts each letter by one position  
### • Example: `a → b`, `b → c`, and so on  


### We are going to learn about more advanced obfuscation methods, as attackers use techniques beyond simple ciphers to hide malicious content.  
### One common technique is XOR, which changes data into unreadable characters and often requires tools like CyberChef to decode accordingly.  
### • Real-world attacks use more advanced obfuscation techniques  
### • XOR modifies each byte using a key to hide the original data 

### Challenge 
### We are going to obfuscate a string using XOR in CyberChef, as this demonstrates how attackers can hide readable data.  
### We will apply the XOR operation to the text `carrot supremacy` using a key and observe the transformed output accordingly.  

### • Open CyberChef in your browser  
### • Enter `carrot supremacy` in the Input section  
### • Search for `XOR` in Operations and add it to the Recipe area  
### • Set the Key to `a` and ensure the Key format is set to `HEX`  
### • Accordingly, the string `carrot supremacy` becomes `ikxxe~*yzxogkis!` after XOR obfuscation  
<img width="1276" height="775" alt="image" src="https://github.com/user-attachments/assets/77a8af73-4fc5-4a75-926b-f28c4d9ce0bb" />

### • `ROT1` → Words appear one letter off while spaces remain unchanged  
### • `ROT13` → Common words become recognizable patterns like `the → gur` and `and → naq`  
### • `Base64` → Long alphanumeric strings, often containing `+`, `/`, and ending with `=` or `==`  
### • `XOR` → Appears as random symbols but usually keeps the same length as the original text  
### • Accordingly, use the reverse CyberChef operation (e.g., `From Base64` for Base64) to deobfuscate the data  
<img width="717" height="461" alt="image" src="https://github.com/user-attachments/assets/ce336b42-a28a-4ab0-a0d4-6d1c1dc4886a" />



### What if we do not recognize the obfuscation technique? We can try different decoding operations in CyberChef until the output becomes readable.  
### Is there an easier way? Yes, CyberChef’s `Magic` operation automatically tests common decoders and suggests possible results accordingly.  
### • Not all obfuscation techniques are easy to identify  
### • Different decoding operations can be tested manually in CyberChef  
### • The `Magic` operation automatically guesses common encoding and obfuscation methods  
### • It displays multiple possible decoded results for analysis  
<img width="910" height="503" alt="image" src="https://github.com/user-attachments/assets/cd60a538-7d09-4b50-afb9-5186a6d781ed" />

### • Attackers commonly combine multiple obfuscation methods together  
### • A script may be compressed with `gzip`, XOR encoded, and then Base64 encoded  
### • This creates a highly obfuscated and unreadable output  
### • Deobfuscation must be performed in reverse order of the applied techniques
<img width="911" height="507" alt="image" src="https://github.com/user-attachments/assets/71cccec4-d1ec-4d0c-abaa-53e8e8caf930" />

### Challenge : Let the fun begin
### We will follow the instructions in the script, run it in PowerShell, and uncover the hidden content to obtain the first flag accordingly.  
### • Open `SantaStealer.ps1` from the Desktop using Visual Studio Code  
### • Navigate to the **"Start here"** section of the script  
### • Follow the instructions provided in the code comments  
### • Save the script and open a PowerShell terminal  
### • Accordingly, run the commands specified in the script comments to reveal the first flag
### Turn on the target machine and open the santastealer.ps1
<img width="960" height="793" alt="image" src="https://github.com/user-attachments/assets/8653be4c-6a46-40ac-9500-8ef40f3c3cf8" />

### Here is the script in Vscode studio
<img width="958" height="788" alt="image" src="https://github.com/user-attachments/assets/049a7348-73f8-43cc-830d-50d0f90a342d" />

### We can observe in part 1 deofuscate the present string in the $C2B64 variable and place the url in C2 variable and run the script to get the flag
### Copy the C2b64 variable to the cyberchef 
<img width="910" height="203" alt="image" src="https://github.com/user-attachments/assets/cfba6331-4a3a-42c0-99c7-20cea2136a3b" />

### We can see the url
<img width="1523" height="577" alt="image" src="https://github.com/user-attachments/assets/e8c76b57-9955-4996-bdf1-891cb832cabb" />

### Now enter the url in the c2 variable in the script 
<img width="881" height="184" alt="image" src="https://github.com/user-attachments/assets/a93908aa-c06c-41aa-8519-59215b03e1f7" />

### Press F5 to run the script 
<img width="897" height="762" alt="image" src="https://github.com/user-attachments/assets/78e418f4-f402-4b21-957b-68dc0173f990" />

### We have received the flag : THM{C2_De0bfuscation_29838}
### Now for the step2 obfuscate the api key using Xor single byte ox37 and convert it in hexdecimal
### Then add hex string to api key and run the script
<img width="904" height="179" alt="image" src="https://github.com/user-attachments/assets/1c01ea08-8603-4b0d-b7b1-e1d134cea346" />

### Copy the api key 
<img width="915" height="381" alt="image" src="https://github.com/user-attachments/assets/01b25607-3c60-4028-8eaf-0c373df236e4" />

### Paste it in the cyberchef and the xor 37 and to the hex receipe
<img width="1362" height="645" alt="image" src="https://github.com/user-attachments/assets/6dc0b491-19f7-4669-b90d-e501b6c68c49" />

### Enter the key inside the script 
<img width="907" height="196" alt="image" src="https://github.com/user-attachments/assets/65d0a403-e21a-40f4-a61d-ecf260561397" />

### Run the script to get the key 
<img width="962" height="289" alt="image" src="https://github.com/user-attachments/assets/f1701992-2ef9-4373-a958-1694ef34a269" />

### We have received the second flag : THM{API_Obfusc4tion_ftw_0283}

<img width="1236" height="343" alt="image" src="https://github.com/user-attachments/assets/1913328b-6d68-4f1d-a3b3-f176bcca31a1" />

### Congratulations !!! We have Successfully Completed the room.
<img width="1239" height="414" alt="image" src="https://github.com/user-attachments/assets/af8f193e-5216-4308-a378-a6043a127077" />
