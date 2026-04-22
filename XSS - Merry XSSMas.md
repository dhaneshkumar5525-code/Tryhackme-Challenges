# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations
### XSS - Merry XSSMas
### Today, We are going to learn about types of XSS vulnerabilities and how to prevent them.
<img width="1752" height="431" alt="image" src="https://github.com/user-attachments/assets/b3c3515e-561b-4c26-8239-cecc54f9eef7" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/5fbbc902-2076-4e0d-b7c5-c3a92c698436" />

### We’re diving into Santa’s newly upgraded workshop where McSkidy’s secure portal is showing strange activity.
### As you can observe, odd messages and coded letters hint that someone is messing with the system—and we’re here to find out who.

### • The workshop was modernized with automation and new tech
### • We have access to McSkidy’s secure message portal
### • Logs show unusual activity and suspicious searches
### • Messages, even Santa’s letters, appear as scripts or random code
### • We will analyze the logs and uncover the source of the mischief

### Learning Objectives
### Understand how XSS works
### Learn to prevent XSS attacks

## Task 2 Leave the Cookies, Take the Payload
### Equipment Check
### For today's room we will be using a the web app found under http://10.48.148.14
### You can use the browser of your AttackBox to navigate to it. You will see a page as shown below:
<img width="2890" height="1698" alt="image" src="https://github.com/user-attachments/assets/b64ce2d1-0856-448f-aec4-da67491204f1" />

### We’re exploring XSS, a web vulnerability where attackers inject malicious code into web applications.
### As you can observe, poor input validation lets this code run in users’ browsers—and we’ll learn how it works.

### • XSS allows injection of malicious JavaScript through input fields (like forms or comments)
### • It occurs when user input is not properly validated or escaped
### • The injected code is executed instead of being treated as plain text
### • This can lead to stolen credentials, page defacement, or user impersonation

### Reflected XSS

### We’re exploring Reflected XSS, where injected code is instantly returned in a web response.
### As you can observe, a crafted URL can execute malicious scripts when a user clicks it.
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/19acdc4a-e8ac-4282-bc80-e1d99f7d4d1c" />

### • Occurs when user input is reflected directly in the response without validation
### • Example normal URL: https://trygiftme.thm/search?term=gift
### • Malicious URL: 
### • https://trygiftme.thm/search?term=<script>alert(atob("VEhNe0V2aWxfQnVubnl9"))</script>
### • The payload runs when the victim clicks the crafted link

### Stored XSS
<img width="1400" height="633" alt="image" src="https://github.com/user-attachments/assets/b25aa30e-19d7-4339-8481-a24a3155e72b" />

### We’re exploring Stored XSS, where malicious scripts are saved on the server and affect every user.
### As you can observe, once injected, the code runs automatically whenever the page is loaded.
### • Occurs when malicious input is stored on the server (e.g., databases, comments)
### • Unlike Reflected XSS, it does not require a crafted link for each victim

### Normal Comment Submission
<img width="1173" height="248" alt="image" src="https://github.com/user-attachments/assets/703b5074-1691-47cc-925e-00a0d903ae94" />

### Malicious Comment Submission (Stored XSS Example)
### If the application does not sanitize or filter input, an attacker can submit JavaScript instead of a comment:
<img width="1401" height="247" alt="image" src="https://github.com/user-attachments/assets/b6163044-23bb-46bd-9243-7b68b8e91b76" />

### • Attackers can act as the victim without their knowledge
### • Can steal session cookies
### • Can trigger fake login popups
### • Can deface or alter the webpage

### Protecting Against XSS
<img width="1278" height="484" alt="image" src="https://github.com/user-attachments/assets/d45f82e8-d1ef-4521-8d16-558408ce0649" />


### We’re learning simple ways to stop XSS by handling user input safely.
### As you can observe, small security steps can prevent harmful scripts from running.

### • Don’t use innerHTML; use textContent to treat input as normal text  
###   → innerHTML can run scripts, while textContent only shows text safely

### • Protect cookies with HttpOnly, Secure, and SameSite settings  
###   → This stops attackers from stealing session data using JavaScript

### • Always clean (sanitize) and encode user input and output  
###   → Removes or converts harmful code before it can run

### • Only allow safe and limited HTML when really needed  
###   → Prevents users from adding dangerous tags like <script>

### • Remove or block scripts and harmful code patterns  
###   → Filters out things like event handlers or JavaScript links

### • We will test this using input fields like the search bar  
###   → XSS needs an input field to inject and run code

### Start the Attack and the Target machine
<img width="918" height="605" alt="image" src="https://github.com/user-attachments/assets/6df8e674-610c-4f22-bf12-a8d2e8ed0b84" />

### Exploiting Reflected XSS 
### We are going to exploiting the reflected xss 
### Enter the target Ip 10.48.148.14 in the search bar to access the machine
<img width="907" height="845" alt="image" src="https://github.com/user-attachments/assets/50f56fe0-8cb4-4439-900c-fbd7d44255c2" />

### Enter the payload in the search bar
### <script>alert('Reflected Meow Meow')</script>
<img width="889" height="565" alt="image" src="https://github.com/user-attachments/assets/c085a88d-f597-4415-a656-5687e4ae93f3" />

### We can see the script has executed and we have captured the Flag: THM{Evil_Bunny}
<img width="903" height="805" alt="image" src="https://github.com/user-attachments/assets/4b554c0e-0324-4ea9-88b5-351eaaf0de93" />

### Navigate to the message form, and enter the malicious payload 
### <script>alert('Stored Meow Meow')</script>
<img width="826" height="338" alt="image" src="https://github.com/user-attachments/assets/0bb4bdde-9b38-480e-a4cc-6a7b562baab1" />

### We can see the flag in recent messages Flag: THM{Evil_Stored_Egg}
<img width="896" height="757" alt="image" src="https://github.com/user-attachments/assets/af2e30cd-1b71-45d4-947a-ffac8da14f37" />

### Answers for the Room
<img width="1621" height="461" alt="image" src="https://github.com/user-attachments/assets/d74419d6-faa7-43c6-999d-23e9341c01cd" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1903" height="441" alt="image" src="https://github.com/user-attachments/assets/b0996012-56c3-43f8-8565-294b79bcf0de" />




















