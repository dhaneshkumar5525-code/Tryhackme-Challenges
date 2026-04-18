# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Today, We are going to Learn about IDOR while helping pentest the TrypresentMe website.
<img width="1903" height="420" alt="image" src="https://github.com/user-attachments/assets/7da4b8df-9d10-48f2-a414-0e306f86b1cf" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/a1e39b55-c9c2-4cc9-939d-4ff18c32d198" />

### The TBFC team investigates suspicious activity on the TryPresentMe website involving stolen vouchers and targeted phishing attacks.
### A malicious account (Sir Carrotbane) was discovered and removed, but deeper vulnerabilities still exist.
### • Users reported issues activating vouchers on the platform  
### • Targeted phishing emails suggest a possible data leak  
### • Suspicious account held multiple stolen vouchers  
### • Account was deleted and vouchers recovered  
### • Further investigation is needed to identify and fix underlying security flaws  

### Learning Objectives

### • Understand authentication and authorization concepts
### • Learn to identify and exploit IDOR vulnerabilities for privilege escalation
### • Spot potential Insecure Direct Object Reference (IDOR) issues  

## Task 2 IDOR on the Shelf
### It’s Dangerously Obvious, Really
### Let’s take a URL like: https://awesome.website.thm/TrackPackage?packageID=1001  
### What if we change the packageID to 11 or 12?
### • We are checking if we can access other users’ data  
### • If it works, it’s an IDOR (access control issue)  
### • The goal is to see if the server properly validates permissions  


### Let’s understand how this works behind the scenes

### We need to look at how applications store and reference data like package IDs  
### For example, a database table might store these package numbers and related details

<img width="1590" height="512" alt="image" src="https://github.com/user-attachments/assets/0a763567-fea4-4a46-9ece-8443f1f63dbe" />


### Let’s see how the application fetches the data

### When we request a package, we provide the packageID, and the server uses it to query the database  
### Example query: SELECT person, address, status FROM Packages WHERE packageID = value;

<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/f7c5cc09-027c-47aa-9fbb-4a4f7f10128b" />


### Authentication vs Authorization

### Authentication means proving who you are (e.g., username and password)  
### Authorization means checking what you are allowed to access after logging in  

###  IDOR happens when authorization checks are missing or weak  
<img width="475" height="384" alt="image" src="https://github.com/user-attachments/assets/ddd1d82a-c53b-450b-a1c6-c52bf6d3cade" />

### Privilege Escalation

### Vertical escalation means gaining higher-level access (e.g., user → admin)  
### Horizontal escalation means accessing other users’ data at the same level  
### • Vertical: performing actions meant for admins  
### • Horizontal: viewing or modifying data that belongs to other users  

### Lets start the lab
<img width="881" height="521" alt="image" src="https://github.com/user-attachments/assets/f84b2be0-5967-4cf6-92a0-7288a5624f3f" />

### Enter the target machine ip 10.48.168.245 to get login page
<img width="941" height="913" alt="image" src="https://github.com/user-attachments/assets/d323822d-800e-4ea2-be44-2636a8a0d4f0" />

### Enter the Username: niels & Password: TryHackMe#2025
<img width="873" height="308" alt="image" src="https://github.com/user-attachments/assets/53e04975-5f4f-4a43-95c3-64d65b37241c" />

### We are logged inside the account
<img width="923" height="861" alt="image" src="https://github.com/user-attachments/assets/0a137ea3-7f18-485f-b522-c2f441a4e91b" />

### Let’s Start Debugging with Developer Tools
### We will use the browser’s Developer Tools to see what is happening behind the scenes  
### Right-click the page and select “Inspect”, then open the “Network” tab  
### Now Let’s Refresh the Page
<img width="920" height="863" alt="image" src="https://github.com/user-attachments/assets/e89bd4bd-7b82-45e9-8bbb-a3dd3bdac464" />

### We will click on the “view_accountinfo” request to see its details  
### This helps us understand what data is being sent and received  
<img width="909" height="841" alt="image" src="https://github.com/user-attachments/assets/f5c8ec5d-8775-4dae-b83e-bd8e9953c46a" />

### We see that the request used user_id = 10  
### When we check the response, it confirms this ID belongs to our account  
<img width="908" height="835" alt="image" src="https://github.com/user-attachments/assets/ac6fa42a-e0bb-4873-b16f-011b498eaa6a" />

### Let’s Modify the User ID
### The app uses user_id to fetch our account data  
### Now we will try changing it to see what happens  
### • Go to Developer Tools → Storage → Local Storage  
### • Find the user_id value  
### • Change it and check if we can access other data  
<img width="901" height="833" alt="image" src="https://github.com/user-attachments/assets/9bdba90d-944d-4235-b32e-c103a50090a9" />

### Navigate to Local Storage
<img width="915" height="833" alt="image" src="https://github.com/user-attachments/assets/e3f91241-4f59-455b-bb87-30c007266c20" />

### The value `Mg==` is just the Base64 encoded form of the number `2`  
### So instead of sending `2`, the application sends it in encoded form  
<img width="914" height="846" alt="image" src="https://github.com/user-attachments/assets/5ebf97fa-52fb-41be-8f38-55ca9cf57a80" />

### Exploiting the IDOR found in the view_accounts parameter, what is the user_id of the parent that has 10 children?
### Automating Requests with Burp Suite
### We use Burp Suite to automate and modify the `view_accounts` request to test for IDOR  
### By changing the `user_id`, we look for the response that shows a parent account with 10 children  
<img width="933" height="623" alt="image" src="https://github.com/user-attachments/assets/2abcaa2f-a50d-4864-90f1-cb738c946f40" />

### Turn the Interceptor on
<img width="962" height="632" alt="image" src="https://github.com/user-attachments/assets/0fdc7bf4-399f-4aeb-a8fe-555a2a90889f" />

### Click View button in Home page
<img width="922" height="855" alt="image" src="https://github.com/user-attachments/assets/ae67b90f-0f43-438b-bef9-910ac5988a5a" />

### Captured the request from browser
<img width="959" height="464" alt="image" src="https://github.com/user-attachments/assets/f0e373fa-b0ca-4e92-a391-671fe8cb6e15" />

### Send the request to the Intruder
<img width="961" height="775" alt="image" src="https://github.com/user-attachments/assets/4ca474aa-13fb-49c1-8ed8-0d306ae25994" />

### Add variables at ID position in intruder
<img width="959" height="626" alt="image" src="https://github.com/user-attachments/assets/f8775e14-e527-470a-b3d7-a009b6b47ca7" />

### In payload section select numbers
<img width="954" height="783" alt="image" src="https://github.com/user-attachments/assets/c3b86ca9-d096-4474-a071-3b833775566b" />

### Payload configurations 0-20
<img width="566" height="309" alt="image" src="https://github.com/user-attachments/assets/d48c75d0-bcba-49ed-8b92-9421785f91f0" />

### Click Start Attack button
### Results are here with http status code
<img width="952" height="723" alt="image" src="https://github.com/user-attachments/assets/d9055a1c-adf5-47a8-8d16-d1ac3d43aad3" />

### Inspecting response by one by one
<img width="775" height="437" alt="image" src="https://github.com/user-attachments/assets/1c93190a-f50f-4ed7-8692-bbf084c44c88" />

### Click and response button
<img width="773" height="438" alt="image" src="https://github.com/user-attachments/assets/844dbde7-024b-419e-a760-c3d8e9acb3cf" />

### Count numbers in childern section 
<img width="769" height="677" alt="image" src="https://github.com/user-attachments/assets/2571bebd-c1db-494b-8a16-1052f422a0c6" />

<img width="761" height="677" alt="image" src="https://github.com/user-attachments/assets/d539adbe-7971-4d7b-8cc1-a5b187c4b074" />

### Exploiting the IDOR found in the view_accounts parameter, what is the user_id of the parent that has 10 children?
### The user_id 15 of the parent that has 10 children
### Answers
<img width="1920" height="609" alt="image" src="https://github.com/user-attachments/assets/57f4ce7d-cd2d-4221-950c-9e626a540fc4" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1919" height="541" alt="image" src="https://github.com/user-attachments/assets/59ffdcca-e134-48ec-b5b1-56e4d989075d" />



