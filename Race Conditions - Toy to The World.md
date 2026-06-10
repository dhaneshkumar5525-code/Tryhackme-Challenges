# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Race Conditions - Toy to The World
<img width="1761" height="423" alt="image" src="https://github.com/user-attachments/assets/17ee1906-cfb0-429c-b324-09a916c6f3d0" />

### Today, we are going to learn how to exploit a race condition attack to oversell the limited-edition SleighToy.
## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/88777a60-4206-4353-9273-163b2491c564" />

### We are going to investigate a checkout system issue, as more customers successfully purchased the limited-edition SleighToy than the available stock allowed.  
### As we can observe, attackers exploited a timing flaw by sending multiple purchase requests simultaneously, resulting in oversold inventory accordingly.  

### • Only 10 SleighToy units were available for sale  
### • Multiple customers received successful purchase confirmations  
### • Several purchases occurred at the exact same moment  
### • Sir Carrotbane’s Bandit Bunnies abused the checkout process with rapid requests  
### • Accordingly, this exposed a race condition vulnerability in the application  

### Learning Objectives  
### • Understand what race conditions are and how they impact web applications  
### • Learn how to identify and exploit race conditions in web requests  
### • Understand how concurrent requests can manipulate stock or transaction values  
### • Explore mitigation techniques to prevent race condition vulnerabilities  

### What is a Race Condition?  
### A race condition occurs when two or more actions happen at the same time, and the final result depends on which action finishes first.  
### As we can observe, if proper synchronization is missing, simultaneous requests can cause unexpected behavior and security issues accordingly.  

### Types of Race Conditions  

### • **TOCTOU (Time-of-Check to Time-of-Use)** → Data is checked first but changes before it is used, such as two users purchasing the same last item simultaneously  
### • **Shared Resource Race Condition** → Multiple users modify the same data at the same time, causing one update to overwrite another  
### • **Atomicity Violation** → A process that should complete as a single operation is interrupted, allowing another request to interfere  
### • TOCTOU commonly affects inventory checks, file access, and transaction validation  
### • Accordingly, all these issues occur due to concurrent operations without proper synchronization  

### Turn on the attack and target machine
<img width="991" height="588" alt="image" src="https://github.com/user-attachments/assets/6a7d1511-0372-42fa-92de-7bdbc884fd65" />

### Open the burpsuite in the attack machine and navigate to the proxy 
<img width="906" height="751" alt="image" src="https://github.com/user-attachments/assets/34e5ebe1-c488-41dc-be9e-62c05d7b7ae8" />

### And interceptor off 
<img width="907" height="673" alt="image" src="https://github.com/user-attachments/assets/00b54b6b-7717-415b-b9ef-2d6f84111535" />

### Click open browser
<img width="907" height="666" alt="image" src="https://github.com/user-attachments/assets/f0cdc21c-07ed-4af0-bbc6-fea1dabcfb03" />

### Enter the Ip 10.65.181.250 in the browser to access login page of he target machine
<img width="909" height="637" alt="image" src="https://github.com/user-attachments/assets/f42ae8d9-b552-42f1-af88-20b21a2c3cbb" />

### Enter the given credentials, username: attacker and password: attacker@123 to login into the account 
<img width="1222" height="99" alt="image" src="https://github.com/user-attachments/assets/fcde7766-f844-4db1-ba06-9fc675aaa199" />

### We are loggedin into the account and we can see  SleighToy Limited Edition stocks 10 and Bunny Plush (Blue) stocks 5 
<img width="904" height="776" alt="image" src="https://github.com/user-attachments/assets/1b853348-c918-41ff-8dbc-c76c4736c3cf" />

### Add both to the cart and click checkout 
<img width="906" height="665" alt="image" src="https://github.com/user-attachments/assets/8320317a-d106-47ed-b8f2-6ea645cfc4c4" />

### Confirm the payment 
<img width="907" height="729" alt="image" src="https://github.com/user-attachments/assets/512c30b1-255e-4561-867d-f5f98da76b54" />

### Now we are back in the shop home page and we can see the stocks are reduced 
<img width="906" height="654" alt="image" src="https://github.com/user-attachments/assets/0287ec30-5570-48c3-bd42-c6b84b073334" />

### Now navigate to the burpsuite proxy >> Http history >> click /process_checkout
<img width="907" height="799" alt="image" src="https://github.com/user-attachments/assets/41a32e43-01ce-4c4d-9c80-cb35af659251" />

### Right click send to the repeater 
<img width="908" height="802" alt="image" src="https://github.com/user-attachments/assets/bf8d1fe0-3bdc-4ead-8325-44037567c085" />

### Open repeater and right click on the tab 1 and new tab group 
<img width="909" height="802" alt="image" src="https://github.com/user-attachments/assets/05b680f3-6fae-4dfe-9a55-50e9a0ffb654" />

### Create group name : Cart
<img width="907" height="666" alt="image" src="https://github.com/user-attachments/assets/e99c36fb-7c77-4d8e-8f24-cb2f6c44b310" />

### We are added in group to send them all at once to cause racecondition
### We can see the group in added and right click on the tab 1 and duplicate tab to send multiple same request at once
<img width="905" height="485" alt="image" src="https://github.com/user-attachments/assets/e551d054-8d55-4740-9b15-977a54519593" />

### We made 70 duplicate tabs
### Make as many as you want which should greater than 10 to make the stock hit negative as per the challenge
<img width="908" height="689" alt="image" src="https://github.com/user-attachments/assets/dc23e71a-7a2f-45ed-8203-36ff852bdfb8" />

### Select send button and send group in parrallel 
<img width="908" height="664" alt="image" src="https://github.com/user-attachments/assets/77d7b505-0a28-48f9-bb55-8fa1a55cfff5" />

### We can see both the stocks went in negative 
<img width="907" height="270" alt="image" src="https://github.com/user-attachments/assets/6e69e602-a3fb-48d4-9012-b34f05a5bfce" />

### We have received the flags 
### Stock 1 : THM{WINNER_OF_R@CE007}
### Stock 2 : THM{WINNER_OF_Bunny_R@ce}

<img width="906" height="745" alt="image" src="https://github.com/user-attachments/assets/e874eb7d-9d55-417e-9730-574e52214c54" />

### Answers for the challenge 
<img width="1253" height="359" alt="image" src="https://github.com/user-attachments/assets/63c4445f-249b-429c-b559-1ae94766577d" />

## Congratulations !!! We have Successfully Completed the room.
<img width="1772" height="424" alt="image" src="https://github.com/user-attachments/assets/6e4c579e-01e1-4f10-95a4-13a5134c8d67" />








