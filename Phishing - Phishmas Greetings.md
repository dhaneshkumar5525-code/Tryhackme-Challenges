# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Phishing - Phishmas Greetings
### Today, we are going to Learn how to spot phishing emails from Malhare's Eggsploit Bunnies sent to TBFC users.
<img width="1238" height="419" alt="image" src="https://github.com/user-attachments/assets/1af995d6-9468-4add-80ae-5e46a8b66d93" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/b73a1d5b-f43e-44e6-aeb5-6e1fb80f3b86" />

### We’re stepping into a situation where TBFC’s email defenses are currently down after McSkidy’s disappearance.
### As you can observe, the SOC team must now manually check every suspicious email.

### • The Email Protection Platform is offline, weakening defenses  
### • Staff must manually triage suspicious messages  
### • SOC team suspects phishing emails are being used to steal credentials  
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/54259792-b2eb-4975-92d3-447cd0ef108c" />

### Incident Response Task

### We’re joining the Incident Response Task Force to help detect phishing emails at TBFC.
### As you can observe, we must carefully decide which emails are safe and which are attacks.

### • We are tasked with identifying legitimate vs phishing emails  
### • Some emails are disguised as normal TBFC work, volunteer sign-ups, or SOC-mas updates 

### Learning Objectives
### Spotting phishing emails
### Learn trending phishing techniques
### Understand the differences between spam and phishing

## Task 2 Spotting Phishing Emails
### Phishing Overview

### • Phishing is an old but still highly effective cyber attack method where attackers trick users into revealing sensitive information  
### • Modern phishing is more advanced, using realistic and well-crafted messages that imitate real people, systems, and internal processes  

### Common Intentions Behind Phishing
### • Credential theft: tricking users into giving passwords or login details 
### • Malware delivery: hiding malicious files or links as safe content  
### • Data exfiltration: stealing sensitive personal or company information  
### • Financial fraud: forcing victims to send money or approve fake invoices

<img width="1485" height="525" alt="image" src="https://github.com/user-attachments/assets/da79d33e-87e4-4238-8dd3-be4bd9c9fa81" />

### We’re analyzing a phishing email where an attacker impersonates an employee to commit fraud.
### As you can observe, even a simple email can bypass strong security by targeting people.

### • Attacker uses a free domain (like gmail.com) to fake an employee identity  
### • Goal is to modify payroll details and perform financial fraud  

### Why Spam Is Not Phishing

### We’re understanding the difference between spam and phishing in simple terms.
### As you can observe, spam is broad and annoying, while phishing is targeted and dangerous.

### • Spam sends bulk messages with no specific target, unlike phishing which targets users  
### • Spam is mostly for promotion, ads, or engagement—not direct attacks  
### • Common spam goals: promoting products, fake offers, and clickbait traffic  

<img width="1475" height="805" alt="image" src="https://github.com/user-attachments/assets/d0e6d252-87e3-45ff-b6c2-2707f8a812d7" />

### The Phishmas Takeover

### We’re exploring common phishing techniques used by attackers to trick users.
### As you can observe, impersonation is a key method to gain trust and deceive victims.

### • Attackers pretend to be trusted people like managers, departments, or services  
### • This builds credibility and makes the email look legitimate  
### • Often marked as urgent to pressure quick action  

<img width="1483" height="641" alt="image" src="https://github.com/user-attachments/assets/86f5bdb4-0e8b-4d06-b2e2-aad5ddb06705" />

### Social Engineering

### We’re learning how attackers manipulate people using social engineering instead of hacking systems.
### As you can observe, emotions and urgency are used to trick users into taking harmful actions.

### • Impersonation: attacker pretends to be McSkidy to gain trust  
### • Sense of urgency: uses words like “urgent” or “immediately” to rush decisions  
### • Side channel: discourages contacting through normal/official communication methods  
### • Malicious intent: aims to steal VPN credentials or sensitive data  
<img width="1482" height="641" alt="image" src="https://github.com/user-attachments/assets/2914d354-b86e-42a7-a2b6-a149883c8231" />

### Typosquatting and Punycode

### We’re learning how attackers trick users using lookalike domains.
### As you can observe, small changes in domain names can easily go unnoticed.

### • Typosquatting: attacker uses misspelled domains (e.g., glthub.com instead of github.com)  
### • Designed to fool users who don’t notice small character changes  
### • Makes fake emails or websites look legitimate  
### • Used to support phishing and impersonation attack
<img width="888" height="452" alt="image" src="https://github.com/user-attachments/assets/eb48b445-89c6-46bd-919f-adc62dd959f6" />

### • Punycode converts Unicode characters into ASCII for domain usage  
### • Attackers replace normal letters with similar-looking ones (e.g., Latin “a” with Greek “α”)  
### • Fake domains can look identical to real ones at first glance  
<img width="632" height="375" alt="image" src="https://github.com/user-attachments/assets/0b21504a-da0b-4ec7-af60-af251ee06c02" />

### Typosquatting & Punycode in Action

### We’re seeing how attackers use lookalike domains to trick users into trusting fake emails.
### As you can observe, small character changes can make malicious domains appear legitimate.

### • Attackers register fake domains similar to real ones to deceive users  
### • These domains are used in phishing emails or fake websites  
### • Example email: "TBFC-IT shared 'Christmas Laptop Upgrade Agreement' with you"  

<img width="1487" height="814" alt="image" src="https://github.com/user-attachments/assets/7849e6d6-de61-4746-9923-571dd1605c33" />

### Email Spoofing

### We’re learning how attackers fake sender identities using email spoofing.
### As you can observe, emails may look legitimate but hide fake details underneath.

### • Email spoofing makes a message appear from a trusted sender  
### • The display name and “From:” field can be misleading  
### • Real sender details can differ in the email headers  
### • Normally, email systems block spoofing—but protections are currently down  
### • Example: "New Audio Message from McSkidy" may contain a spoofed sender  

<img width="1477" height="483" alt="image" src="https://github.com/user-attachments/assets/7bf10a08-296f-4b3b-a28f-25c83fe3f030" />

### It looks like a real domain from TBFC, but let's check some essential fields in the email headers:

### Authentication-Results
### Return-Path
<img width="1433" height="418" alt="image" src="https://github.com/user-attachments/assets/354eae00-7a31-4bd5-aebe-905c0c94d6ef" />

### Email Authentication Checks

### We’re learning how to verify if an email is real using security checks.
### As you can observe, failed checks clearly indicate a spoofed email.

### • SPF: defines which servers are allowed to send emails for a domain  
### • DKIM: adds a signature to ensure the email is not altered  
### • DMARC: decides what to do if SPF/DKIM checks fail  
### • If SPF and DMARC both fail, the email is likely spoofed 

### Legitimate Applications Abuse

### We’re learning how attackers misuse trusted platforms to deliver phishing attacks.
### As you can observe, legitimate-looking links can still lead to malicious actions.

### • Attackers use trusted services (e.g., cloud sharing platforms) to appear legitimate  
### • Emails often include attractive offers like salary raises or device upgrades  
### • Links redirect users to fake documents or pages  

<img width="1510" height="733" alt="image" src="https://github.com/user-attachments/assets/07495cbc-c176-4d7a-8048-6d3d4bcc0185" />

### Fake Login Pages

### We’re learning how attackers use fake login pages to steal credentials.
### As you can observe, these pages often look identical to real login portals.
<img width="1917" height="965" alt="image" src="https://github.com/user-attachments/assets/49d7de9b-1691-4227-8c11-fca6ddf4d95e" />

### Above it's a Fake Microsoft Login Page sample. 
### We can observe the fake domain microsoftonline.login444123.com/signin at the top.

### Side Channel Communications

### We’re learning how attackers move conversations outside email to avoid detection.
### As you can observe, shifting to other platforms helps them continue social engineering freely.
<img width="1508" height="429" alt="image" src="https://github.com/user-attachments/assets/5ce371ae-96ba-4e66-8689-a19ab2f990ba" />

## Lets get to the fun part : Pratical
### Turn the Target machine 10.48.141.55
<img width="1611" height="332" alt="image" src="https://github.com/user-attachments/assets/3ac5846b-4203-4994-b8ec-01e5cd411c43" />

### We can access the machine using the link below
### https://10-48-141-55.reverse-proxy.cell-prod-ap-south-1a.vm.tryhackme.com/
### the link takes to the Wareville Email Threat Inspector
### there are 6 mails 
### Lets start the investigation

### First mail 
### From "service@paypal.com" <service@paypal.com> To "naeryn@tbfc.com" <naeryn@tbfc.com>
### Subject: Invoice from Santa Claus (4103)
<img width="1351" height="738" alt="image" src="https://github.com/user-attachments/assets/955fb3b9-f491-40d6-937d-118e455784de" />

### Email claims it is from the paypal invoice for $699.89 USD and no attchment
### lets analyze the email header
<img width="1305" height="535" alt="image" src="https://github.com/user-attachments/assets/85575f88-a214-4390-9996-f6fdb5f12bae" />

### We can see Authentication-Results both spf and dkim is failed 
<img width="910" height="403" alt="image" src="https://github.com/user-attachments/assets/07057325-0ef1-42d4-8b43-3303eb491338" />

### And the return path is 	bounces+SRS=qVbic=PZ@bbunny378.onmicrosoft.com
### Links found 
<img width="1324" height="831" alt="image" src="https://github.com/user-attachments/assets/5a8c74ec-8c79-4fb9-83d4-a9d30d191c23" />

### Submit the report 
<img width="1313" height="492" alt="image" src="https://github.com/user-attachments/assets/f09f397e-e72e-469f-b16b-489c2658fe36" />

### We have received the flag THM{yougotnumber1-keep-it-going}
<img width="1288" height="175" alt="image" src="https://github.com/user-attachments/assets/7cab906b-5654-47b1-9975-b680047f5e71" />

### Second mail
### From McSkidy Missed Call Notifier <calls@tbfc.com> To tarron@tbfc.com
### Subject: New Audio Message from McSkidy
<img width="840" height="685" alt="image" src="https://github.com/user-attachments/assets/71ace196-1397-480e-827d-33fe0219fe75" />

### There is a Attachment
<img width="789" height="222" alt="image" src="https://github.com/user-attachments/assets/caa43056-1719-4fbf-be62-25911d573758" />

### The Attachment is malicous .html
### Lets examine the Authentication-Results
<img width="1295" height="391" alt="image" src="https://github.com/user-attachments/assets/8c7543e3-f2be-43e6-8c16-7f46fa2b9914" />

### Both spf and dkim is failed and the Return-Path	zxwsedr@easterbb.com
### Results spoofing

### This is a phishing attack
<img width="1312" height="649" alt="image" src="https://github.com/user-attachments/assets/b6b21c85-6dba-4cf4-8aea-a5c792fd02aa" />

### We have captured the flag THM{nmumber2-was-not-tha-thard!}

### Lets head towards the third mail
### From McSkidy <mcskiddyy202512@gmail.com> To TBFC Blue Team <blueteam@tbfc.com>
### URGENT: McSkidy VPN access for incident response
<img width="1378" height="786" alt="image" src="https://github.com/user-attachments/assets/21380a05-3a4d-4252-9eb1-93b69e5d94bc" />

### We can see the Sense of Urgency in the mai
### No attachments
### Lets examine the Authentication-Results
<img width="1317" height="544" alt="image" src="https://github.com/user-attachments/assets/ca64c1ac-a73b-4b22-9eb9-51f36694eb32" />

### Both spf and dkim is passed and the Return-Path	mcskiddyy202512@gmail.com
### This a phishing attack
<img width="1311" height="641" alt="image" src="https://github.com/user-attachments/assets/190684dd-f0d9-4d61-a301-608b0f1657db" />

### We have captured the Flag: THM{Impersonation-is-areal-thing-keepIt}

### Fourth mail
### From TBFC HR Department <no-reply@dropbox.com> To Neymar Junior <neymar.junior@tbfc.com>
### Subject: TBFC HR Department shared "Annual Salary Raise Approval.pdf" with you
<img width="1349" height="896" alt="image" src="https://github.com/user-attachments/assets/ddeff671-3ace-47d3-b449-2966c38cf3f8" />

### No attachment 
### Lets examine the Authentication-Results 
<img width="1305" height="463" alt="image" src="https://github.com/user-attachments/assets/0d5b4dad-11b3-489b-9279-0ae68b733a0d" />

### Both spf and dkim is passed and the Return-Path	345675444334263@email.dropbox.com
### These are the detected links
<img width="999" height="631" alt="image" src="https://github.com/user-attachments/assets/17dcf334-e9b0-49ac-b9c5-a5291ee596e6" />

### This is a phishing attack
<img width="1301" height="645" alt="image" src="https://github.com/user-attachments/assets/1c935dc6-e912-408a-9358-33df905c4c03" />

### We have captured the Flag: THM{Get-back-SOC-mas!!}

### Fifth mail
### From Lara <lara@candycane-co.wv> To TBFC Events <events@tbfc.com>
### Subject: Improve your event logistics this SOC-mas season

<img width="1313" height="746" alt="image" src="https://github.com/user-attachments/assets/45777f75-4f95-4b69-96cd-1ef553eafac6" />

### No attachment
### Lets examine the Authentication-Results
<img width="1302" height="377" alt="image" src="https://github.com/user-attachments/assets/6000cbfd-4f26-4493-b66e-1a7f3c54ffde" />

### Both spf and dkim is passed and Return-Path	candycane-co.wv
### It is a spam
<img width="1307" height="252" alt="image" src="https://github.com/user-attachments/assets/5bbd7b4e-31bc-48f1-bf4f-ca911460d9fd" />

### We have captured the  Flag: THM{It-was-just-a-sp4m!!}

### Sixth mail
### From TBFC-IT <tbfc-it@tbƒc.com> To Savoy <savoys@tbfc.com>
### If you observe closely it is a latin "f" letter
### Subject: TBFC-IT shared "Christmas Laptop Upgrade Agreement" with you
<img width="1308" height="750" alt="image" src="https://github.com/user-attachments/assets/eebb5779-ad4b-492d-bf00-edc73b9002b9" />

### No attachment 
### Lets examine the authentication-results
<img width="1312" height="484" alt="image" src="https://github.com/user-attachments/assets/c5d6741e-947f-473e-81f0-d93ec831107a" />

### Both spf and dkim is passed and Return-Path	tbfc-it@xn--tbc-n5a.com
### Links detected from the maiL
<img width="1201" height="685" alt="image" src="https://github.com/user-attachments/assets/cd6171ae-c8b3-47b4-9d4c-7aeb374ffd7d" />

### It is a phishing attack
<img width="1310" height="634" alt="image" src="https://github.com/user-attachments/assets/47b2e1b3-9191-44df-ba32-77d580fe3086" />

### We have captured the Flag:THM{number6-is-the-last-one!-DX!}

### Here are the answers from the room
<img width="1611" height="813" alt="image" src="https://github.com/user-attachments/assets/f518eb56-72c8-4bc3-baef-8490eedead3a" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1798" height="423" alt="image" src="https://github.com/user-attachments/assets/72cc1f3e-7d82-4f7d-8133-a696bc00fc30" />


