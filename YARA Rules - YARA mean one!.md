# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### YARA Rules - YARA mean one!
### Today, we are going to learn how YARA rules can be used to detect anomalies.
<img width="1765" height="426" alt="image" src="https://github.com/user-attachments/assets/e5b78fed-83c7-4799-a42a-043562d4372d" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/b737c28b-9263-41be-a12f-406d31638837" />

### We are going to analyze McSkidy’s disappearance, as we can observe she used images to send hidden messages, resulting this indicates covert communication.  
### We are going to use a YARA rule to detect keyword–code word patterns, as we can observe this helps extract and decode the message accordingly.  

### • McSkidy sent anonymous Easter-themed images to help the blue team  
### • As we can observe, images contain hidden messages  
### • We are going to scan using a YARA rule for keyword–code word patterns  
### • Resulting this, we extract code words  
### • Accordingly, arranging them reveals the final message  

### Learning Objectives
### Understand the basic concept of YARA.
### Learn when and why we need to use YARA rules.
### Explore different types of YARA rules.
### Learn how to write YARA rules.
### Practically detect malicious indicators using YARA.

## Task 2 Yara Rules
### We are going to understand YARA, as we can observe it is used to identify and classify malware using unique patterns, resulting this helps detect threats effectively.  
### We are going to use YARA in our investigation, as we can observe it scans files, code, and memory to uncover hidden malicious activity accordingly.  
<img width="1496" height="995" alt="image" src="https://github.com/user-attachments/assets/0dfe3c88-72c5-4056-9ad2-0a8a14f24683" />
 
### • YARA works by detecting patterns, acting like digital fingerprints of attackers  
### • As we can observe, it helps analysts identify malware based on known signatures  
### • Within TBFC, YARA acts as a silent guardian scanning systems for threats  

### Why YARA Matters and When to Use It  

### We are going to understand why YARA is important, as we can observe many threats hide as normal files, resulting this makes detection difficult without pattern-based analysis.  
### We are going to apply YARA in different scenarios, as we can observe it enables custom rule-based detection and improves threat hunting accordingly.  
### • YARA detects malware based on behavior and patterns, not just names  
### • As we can observe, defenders can create and customize their own detection rules  
### • Shared YARA rules from other defenders can be used and improved  

### YARA Rules  

### We are going to understand how YARA rules work, as we can observe they help uncover malicious patterns, resulting this helps identify threats effectively.  
### We are going to break down the components of a YARA rule, as we can observe each part plays a role in detection accordingly.  
### • Metadata contains details like author, date, and purpose of the rule  
### • As we can observe, strings act as clues such as text, byte sequences, or regex patterns  
### • Conditions define the logic for when the rule should trigger  

### Here’s how it looks in practice:
<img width="782" height="421" alt="image" src="https://github.com/user-attachments/assets/3061e17c-1dea-4855-bb74-60592b9905f2" />

### YARA Strings Explanation
### • In the `strings:` section, I define the patterns that YARA should search for inside the file.
### • I use `$a` as the identifier name for the string pattern so I can reference it in the rule.
### • `"cmd.exe"` is the actual suspicious text that I want YARA to detect.
### • I add `ascii` to tell YARA to search for this text in normal readable text format.
### • This rule helps me check whether the file contains `cmd.exe`, which can indicate suspicious or malicious activity.

### Case-Insensitive Strings – `nocase`
<img width="773" height="88" alt="image" src="https://github.com/user-attachments/assets/f8c1cddb-35a3-4a11-9b8a-3cce4977efe3" />

### • By default, YARA checks the exact same letters, including capital and small letters.
### • I use `nocase` to make YARA ignore uppercase and lowercase differences.
### • For example, `"Christmas"`, `"christmas"`, and `"CHRISTMAS"` will all match.
### • This is useful because malware may change letter case to avoid detection.
### • `nocase` helps me detect the same word even if the writing style is different.

### Wide-Character Strings – `wide`, `ascii`
<img width="769" height="92" alt="image" src="https://github.com/user-attachments/assets/38f7fd34-2da5-41f7-ac81-19000281f672" />

### • Many Windows files store text in Unicode format using two bytes for each character.
### • I use `wide` to tell YARA to search for strings in Unicode format.
### • I use `ascii` to search for normal single-byte readable text format.


### XOR Strings – `xor`
<img width="777" height="94" alt="image" src="https://github.com/user-attachments/assets/43e05ece-8e4b-4133-9496-47303b5f109b" />

### • I use `xor` when malware hides text using XOR encoding to avoid detection.
### • YARA checks all possible single-byte XOR versions of the string automatically.
### • This helps detect hidden malicious text like `$hidden = "Malhare" xor`.

### Base64 Strings – `base64`, `base64wide`
<img width="769" height="93" alt="image" src="https://github.com/user-attachments/assets/c89a0e97-3717-48b7-90b4-629e489634f0" />

### • I use `base64` when malware hides commands or payloads using Base64 encoding.
### • YARA searches for the original text even if it is stored in encoded form.
### • This helps detect hidden strings like `$b64 = "SOC-mas" base64`.


### Lets start the practical 
### Mcskidy sent a message in the form on files downloaded in downloads folder
### Navigate to the downloads and look at the image files
<img width="1410" height="579" alt="image" src="https://github.com/user-attachments/assets/72024001-face-4775-b5aa-7944bd13235f" />

### Lets find the hidden message from mcskidy
### Paste the yara rule in a file using the nano command
<img width="847" height="562" alt="image" src="https://github.com/user-attachments/assets/2dd9389d-6f4a-466a-903b-134163c0c14d" />

### Here is the modified rule /TBFC:[A-Za-z0-9]+/ ascii string
### This string listout letters of capital and small and numbers and plus for remaining
### Ascii is helps the string where to looks. Ascii is a normal readable format
<img width="844" height="559" alt="image" src="https://github.com/user-attachments/assets/0027cab2-f4a2-4fb0-8fe8-e3949477b1da" />

### The pratical example of string works using regex 101
<img width="1519" height="324" alt="image" src="https://github.com/user-attachments/assets/4431a453-3db6-4450-9fa6-d747126d96f1" />

### Save the rule on the desktop
### To Run the rule enter the command : yara -rs  /home/ubuntu/TBFC_Simple_MZ_Detect /home/ubuntu
### Command breakdown
### yara -rs = Recursive search
### /home/ubuntu/TBFC_Simple_MZ_Detect = Rule path
### /home/ubuntu = Target path
 <img width="845" height="557" alt="image" src="https://github.com/user-attachments/assets/086c6d72-a558-4125-8e03-49a9201797f6" />

### We can see the results 5 .jpg files
### Each message contains a single word of the message from mcskidy
### Together : HopSec Find me Island In

### Here are the answers for the path
<img width="1611" height="476" alt="image" src="https://github.com/user-attachments/assets/245bfdec-5688-41ef-8a8f-e1efcac96e9e" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1777" height="418" alt="image" src="https://github.com/user-attachments/assets/62aa0832-c458-40a5-b6c4-fc200c9d2c30" />
















