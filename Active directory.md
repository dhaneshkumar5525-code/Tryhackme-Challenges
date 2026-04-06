# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.

<img width="750" height="422" alt="image" src="https://github.com/user-attachments/assets/99fa6eba-8893-4f4f-b9f0-a98e52106525" />

### “In Active Directory, real impact comes from fixing the small things attackers rely on.”
### This room will introduce the Active concepts and functionality provided by Active Directory.

## Task 1: Introduction:
<img width="1870" height="946" alt="image" src="https://github.com/user-attachments/assets/86b23aa1-7be1-4446-93aa-64fb82bef9c8" />

### Microsoft's Active Directory is the backbone of the corporate world. It simplifies the management of devices and users within a corporate environment. 
### In this room, we'll take a deep dive into the essential components of Active Directory.

## Task 2: Active Directory Overview
<img width="1738" height="912" alt="image" src="https://github.com/user-attachments/assets/4202f4d6-9e3d-43cf-8fc5-5334435e73cf" />

### Windows Domain: A group of users and computers under the administration of an organization.  
### Active Directory: Enables a domain to centrally manage all components of a Windows network.  
### Domain Controller(DC): The server that runs Active Directory services.  

### Advantages of Active Directory:
### - Centralized identity management,
### - Managing security policies efficiently. 
<img width="1640" height="340" alt="image" src="https://github.com/user-attachments/assets/c46b8ebd-8692-4e86-8180-a02a21b0c306" />

## lets start the Attack Box:

<img width="1560" height="639" alt="image" src="https://github.com/user-attachments/assets/f44ef2e3-8aa7-47be-b8a1-12e88d63e5ce" />

## Task 3: Active Directory Domain Services (AD DS)


### **Active Directory Domain Service (AD DS):**  Acts as a catalog holding information about all "objects" on your network — users, groups, machines, printers, shares, and more.

 ### Users in Active Directory: 
 ### - Common objects and security principals (can be authenticated and assigned permissions).  
 ###  - Can access network resources like files and printers.  
 ###  Represent: 
 ###   - People (e.g., employees),  
 ###  - Services (e.g., IIS, MSSQL).
## Key Components:

### Service Accounts:
### - Accounts with limited permissions, assigned to specific services based on their role.

### Machine Accounts: 
###  - Every computer joined to Active Directory has a machine account.  
###  - Machines function like users and can access network resources.  
### - Each machine is a local administrator on its own system.  
### - These accounts are typically not used for human logins.  
### - Passwords are automatically managed and highly complex.  
### - Naming convention: ends with `$` (e.g., `DC01$`). 
### Security Groups in Active Directory:
### -Allow assigning permissions to multiple users, computers, or groups at once
### -Reduce the need for individual permission management
### -Improve administrative efficiency and consistency
### -Help minimize configuration errors
### Examples of Security Groups:

<img width="1584" height="639" alt="image" src="https://github.com/user-attachments/assets/50f4dd34-d515-4fd9-b0ec-eb534d3ca758" />

### Accessing Active Directory Users and Computers (ADUC)
### -Start the attack machine >Open the Start menu >Search for Active Directory Users and Computers (ADUC) >Launch the tool to manage users, groups, and organizational units

<img width="415" height="675" alt="image" src="https://github.com/user-attachments/assets/03610545-8599-4b2a-b515-7529fa61e097" />

### ADUC Window:
### - Displays domain hierarchy (users, computers, groups)

### Organizational Units (OUs):
### - Container objects to organize users and machines.  
### - Help classify and manage resources.

### Purpose of OUs:
### - Group users with similar policy requirements.
### - Simplify administration and control.  

### OU vs Security Groups:

###  Purpose:
### - OU Used to apply policies and organize users/computers. 
### - Security Groups Used to assign permissions to resources. 

###  Membership:
### - OU: A user can belong to only one OU. 
### - Security Groups: A user can belong to multiple groups.

###  Usage:
### - OU Helps in management and policy enforcement.
### - Security Groups Controls access to shared resources (files, printers). 

<img width="1618" height="490" alt="image" src="https://github.com/user-attachments/assets/d597f67f-b5c2-43e2-995d-28288ab7407c" />

## Task 4: Managing Users in AD
### Your first task as the new domain administrator is to check the existing AD OUs and users, as some recent changes have happened to the business.

<img width="1542" height="702" alt="image" src="https://github.com/user-attachments/assets/57620cd2-3253-44fc-a1d0-f91edef94deb" />

###  Task to Deleting Objects in ADUC:
### - Remove objects as per organizational changes.
### - ADUC prevents accidental deletion by default.

<img width="404" height="159" alt="image" src="https://github.com/user-attachments/assets/ff3d29db-6d14-4074-ad65-7bd566a94a78" />

###   Steps:  
### - Enable **Advanced Features** in **View** menu. 

<img width="754" height="417" alt="image" src="https://github.com/user-attachments/assets/06b4e11a-930a-4ed1-a1dd-80d4d8721844" />

### - Uncheck **Protect from accidental deletion**.  

inset image of delecting user



<img width="420" height="472" alt="image" src="https://github.com/user-attachments/assets/bcdb6089-c595-449b-bf28-ea75ac1694ba" />

### - Delete the user or object.

### Delegation:
### - Allows giving specific users control over certain OUs  
### - Grants users privileges to perform tasks on OUs  
### - No need for Domain Administrator intervention  
### - Helps delegate management safely and efficiently
## Delegating Control in ADUC -Assigning Delegation:

### - Navigate to the Organizational Unit (OU)  
### - Right-click the OU and select **Delegate Control**

<img width="311" height="372" alt="image" src="https://github.com/user-attachments/assets/04b695c5-2c19-4457-a675-cd9aae11d7e8" />

### - Click **Next**, then select the user or group 

<img width="583" height="570" alt="image" src="https://github.com/user-attachments/assets/706169a7-8677-4413-ad46-249b5e1bb56c" />

### - Use **Check Names** to verify there are no typos, then click **OK**  
### - Assign task: **Reset user passwords**  
### - Select **Force password change at next login**, click **Next** and then **Finish**

<img width="531" height="414" alt="image" src="https://github.com/user-attachments/assets/e9415096-e0a3-4dca-a048-1086ac2abc41" />

### - Result: User (e.g., Phillip) can now reset passwords for users in that OU

### Now let's use Philip's account to try and reset Sophie's password. Here are Phillip's credentials for you to log in via RDP:
###  Connecting to the Attack Machine using this credentials 
### Username:	philip
### Password:	Claire2008

<img width="1100" height="462" alt="image" src="https://github.com/user-attachments/assets/405f0e43-8f06-43b6-a806-6d273526290f" />

### Open the Powershell as philip and use this command:
### PS C:\Users\phillip> Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose
### New Password: Sophie!1924*
### Since we wouldn't want Sophie to keep on using a password we know, we can also force a password reset at the next logon with the following command:
### PS C:\Users\phillip> Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose

<img width="633" height="439" alt="image" src="https://github.com/user-attachments/assets/01373649-0f94-4c30-b266-8d7a4f2a3255" />

### Now Login into the Username:Sophie and Password:Sophie!1924*
<img width="642" height="479" alt="image" src="https://github.com/user-attachments/assets/439d900f-cda3-45a9-8af9-92a9627de89f" />

In the Destop there is a THM FLAG!!!

<img width="986" height="558" alt="image" src="https://github.com/user-attachments/assets/5ecc3682-e6fc-45ba-9033-f3b4c9503471" />
<img width="1638" height="344" alt="image" src="https://github.com/user-attachments/assets/0405055e-1a3b-4ae0-bedf-1d64b1fb24e1" />

##Task 5: Managing Computers in AD
### Organizing Devices in Active Directory

### - No strict rule, but best practice is to group devices by purpose  

### Device Categories 

### - Workstations  
### - Used by users for daily tasks and browsing  
### - Should not have privileged users logged in  

### - Servers  
### - Provide services to users or other systems  

### - Domain Controllers  
### - Manage the Active Directory domain  
### - Most sensitive systems (store hashed passwords)  

### OU Setup

### - Create separate OUs for **Workstations** and **Servers**

<img width="919" height="750" alt="image" src="https://github.com/user-attachments/assets/1aa6192d-32f0-40cd-9e67-ad798c399e50" />


### - Domain Controllers OU already exists by default  
### - Create OUs under the domain (e.g., **thm.local**)  

<img width="754" height="366" alt="image" src="https://github.com/user-attachments/assets/49ba7e11-5083-4e5b-8153-9aa2dc4dbaf7" />

### Now, move the personal computers and laptops to the Workstations OU and the servers to the Servers OU from the Computers container. Doing so will allow us to configure policies for each OU later.

<img width="680" height="558" alt="image" src="https://github.com/user-attachments/assets/5335f7a0-fa97-4381-b558-580e5783ccfd" />
<img width="1635" height="344" alt="image" src="https://github.com/user-attachments/assets/93696c2b-a512-4a04-bea2-dd3ea311a141" />

### Group Policy Objects (GPO)

### - Windows uses GPOs to manage policies  
### - GPOs are collections of settings applied to OUs  
### - Can target users or computers  
### - Helps enforce security and configuration baselines  

### Configuring GPOs

### - Open **Group Policy Management** from the Start menu  

<img width="386" height="676" alt="image" src="https://github.com/user-attachments/assets/a1ae9036-ae2e-48b9-afde-8b1aa9339a3f" />
<img width="954" height="577" alt="image" src="https://github.com/user-attachments/assets/4bcda173-67cd-41f7-9989-6b35b185dc0f" />

### We are going to change the password Policy:
### Navigate to the Setting Tab and Click Computer Configuration (enabled) > Account Policy/Password Policy
<img width="578" height="405" alt="image" src="https://github.com/user-attachments/assets/b28a5a29-f128-4387-8537-c429e9366bff" />

### Minimum Password Length is 7 Characters -- We have to change it to Minimum 10 Characters
<img width="957" height="584" alt="image" src="https://github.com/user-attachments/assets/40010e70-63f6-4d22-ba6b-adf487e3f06c" />

###  go to Computer Configurations -> Policies -> Windows Setting -> Security Settings -> Account Policies -> Password Policy and change the required policy value:

<img width="957" height="584" alt="image" src="https://github.com/user-attachments/assets/d33277eb-0675-43b6-95da-d080216e6feb" />
### Change to 10 Characters

<img width="961" height="684" alt="image" src="https://github.com/user-attachments/assets/0ba9d9bf-df6a-4e5d-b3d9-0f3c54ff2f88" />

### GPO Distribution

### - GPOs are distributed via the **SYSVOL** share on Domain Controllers  
### - Located at: C:\Windows\SYSVOL\sysvol\  
### - Domain users access it to sync policies  

### - GPO updates may take up to 2 hours  
### - Use **gpupdate /force** to apply changes immediately  
<img width="1610" height="137" alt="image" src="https://github.com/user-attachments/assets/d767009d-4486-41ee-8774-138fa0f85054" />

### Creating GPOs (THM Inc.)--Sub Task:

### 1) Block non-IT users from accessing Control Panel  
###    Apply to user accounts (link to user OU)    

### User Configuration > Administrative Templates > Control Panel > Prohibit access to Control Panel and PC settings > enter.
<img width="821" height="669" alt="image" src="https://github.com/user-attachments/assets/a47ca472-9cda-444f-9ec9-f679d9e5511b" />

## Enable this Setting- Prohibit access to Control Panel and PC settings.
<img width="798" height="771" alt="image" src="https://github.com/user-attachments/assets/78d7ceaa-f632-4f33-93c3-1452ee717c02" />

## Creating a Group Polices using Group Policy Management (GPO):
## Group Policy Management > thm.local > Right-click > Create a GPO in this domain, and Link it here Option.

<img width="949" height="501" alt="image" src="https://github.com/user-attachments/assets/f3e20f9d-c472-4d81-ad14-2d88c66e745e" />

 ## Enter the New GPO Name:
<img width="492" height="304" alt="image" src="https://github.com/user-attachments/assets/5a10928b-53b0-4b2f-b1f4-4b88962e4b56" />

## New Gpo Created and Select the Gpo and drag to the Organization Unit(sales) and Select it.
<img width="960" height="599" alt="image" src="https://github.com/user-attachments/assets/65250b84-eba7-4509-bce9-161588659655" />

## Do the Same for the Marketing and Management:
<img width="310" height="440" alt="image" src="https://github.com/user-attachments/assets/601982f4-159c-4127-81d7-ba1812eea3bf" />

### 2) Auto-lock devices after 5 minutes of inactivity  
###  Apply to computers (link to Workstations & Servers OUs)  

### Modify the Existing Gpo - Account Lock Screen:
<img width="966" height="238" alt="image" src="https://github.com/user-attachments/assets/1389413a-7e5c-4cfc-b03f-cccefafa0343" />

### Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options and Select Account Lockscreen.
<img width="787" height="565" alt="image" src="https://github.com/user-attachments/assets/acb572bb-1c2c-47e3-9511-3e13c53fe573" />

### Change to 300 Seconds:
<img width="495" height="585" alt="image" src="https://github.com/user-attachments/assets/3844f4b4-b52e-4e25-8b7f-0b3915d4573a" />

### Link to the Required Organizational Units.

<img width="1664" height="337" alt="image" src="https://github.com/user-attachments/assets/4dea3d63-4f35-46ec-867a-1c41b2008ccf" />

## Task 7: Authentication Methods:
### Windows Domain Authentication

### - All credentials are stored on **Domain Controllers**  
### - Services verify user credentials with the Domain Controller  

### - **Kerberos:** Default protocol for modern Windows domains  
### - **NetNTLM:** Legacy protocol for compatibility purposes

### Kerberos Authentication Steps:

### - **Step 0: Pre-Authentication Check**  
### - User sends username to KDC  
### - KDC may require pre-authentication (KRB5_PREAUTH_REQUIRED)
<img width="1082" height="542" alt="image" src="https://github.com/user-attachments/assets/e26b895f-d321-4e2d-9c37-8d0795e79c89" />


### - **Step 1: AS-REQ (Authentication Service Request)**  
### - User sends username + timestamp encrypted with password hash  
### - KDC decrypts and verifies timestamp to prevent replay attacks  
<img width="1100" height="628" alt="image" src="https://github.com/user-attachments/assets/cd0accad-7754-489e-9412-ab3abb95a3be" />

### Even if the Attacker Steals the AS-REQ and uses it to decrypt message but Timestamp does not match 

### - **Step 2: AS-REP (Authentication Service Response)**  
### - KDC issues **TGT (Ticket Granting Ticket)** and **Session Key**  
### - TGT encrypted with krbtgt account hash; Session Key encrypted with user key 

<img width="1082" height="543" alt="image" src="https://github.com/user-attachments/assets/061ab33f-d0da-4d43-a926-fb14fcd36454" />



### - **Step 3: TGS-REQ (Ticket Granting Service Request)**  
### - User requests service ticket with TGT + Authenticator + SPN (service name)  
### - KDC decrypts TGT, verifies Authenticator  
<img width="1090" height="538" alt="image" src="https://github.com/user-attachments/assets/2e6ee7fe-92de-4fb5-a76e-46b95a5db7aa" />


### - **Step 4: TGS-REP (Ticket Granting Service Response)**  
### - KDC issues **Service Ticket** for the requested service  
### - New session key provided for secure communication 
<img width="1090" height="538" alt="image" src="https://github.com/user-attachments/assets/fd1f4650-97b3-413a-b99a-395af617cf7c" />


### - **Step 5: AP-REQ (Application Request)**  
### - User sends Service Ticket + Authenticator to service  
### - Service decrypts and verifies identity  
<img width="1100" height="535" alt="image" src="https://github.com/user-attachments/assets/01b1af54-62e4-4d17-912a-4db98f309da7" />


### - **Step 6: AP-REP (Application Response)**  
### - Service responds using session key  
### - User verifies service and gains secure access
<img width="1100" height="535" alt="image" src="https://github.com/user-attachments/assets/4c0092d2-5b2b-4057-90f9-d34c5382a2e8" />


### - **Key Benefits**  
### - Single Sign-On (SSO): Authenticate once, use multiple services  
### - Centralized Authentication: Passwords never transmitted  
### - Secure Access: Prevents replay attacks, protects credentials  
### - NTDS.dit stores password hashes for verification by KDC

### NTLM Authentication Steps:
<img width="1100" height="619" alt="image" src="https://github.com/user-attachments/assets/68d5b7f5-d851-4f3d-aebc-d40368496655" />


### - **Client Request:** Client asks the server to authenticate it  
### - **Server Challenge:** Server sends a random challenge to the client  
### - **Client Response:** Client encrypts challenge with password hash and returns it  
### - **Server Verification:** Server calculates expected response using stored hash  
### - If responses match, client is authenticated and access is granted
<img width="1629" height="447" alt="image" src="https://github.com/user-attachments/assets/f7da7df5-e2db-410c-8aca-cea61986cf71" />

### So far, we have discussed how to manage a single domain, the role of a Domain Controller and how it joins computers, servers and users.

<img width="641" height="384" alt="image" src="https://github.com/user-attachments/assets/1e8c1d31-b0c2-4151-a956-9f2ae5eca394" />

### Trees in Active Directory

### - Used to manage large or expanding organizations  
### - Allows multiple domains to be grouped together  

### - Domains in a tree share the same namespace  
### - Example: thm.local → uk.thm.local, us.thm.local  

### - Each domain has its own users, computers, and policies  
### - Enables independent management for different regions (e.g., UK, US)  

<img width="1218" height="963" alt="image" src="https://github.com/user-attachments/assets/fae75089-8dd0-458f-bcd3-6a059d8c34e3" />

### Forests in Active Directory

### - Collection of multiple domain trees  
### - Trees can have different namespaces  

### - Used when organizations merge (e.g., THM Inc. + MHT Inc.)  
### - Each tree can be managed independently  

### - All trees together form a single forest  

<img width="2778" height="1119" alt="image" src="https://github.com/user-attachments/assets/fb57a2f0-3e15-4451-812a-b77ba88e7ac6" />

### Trust Relationships

### - Connect domains to allow resource sharing  
### - Enable users from one domain to access another domain  

### - **One-way trust:**  
### - Domain AAA trusts BBB → Users in BBB can access AAA  

### - **Two-way trust:**  
### - Both domains trust each other  
### - Users in both domains can access resources  

### - Trust does not give automatic access  
### - Access must be explicitly granted to users  

<img width="963" height="386" alt="image" src="https://github.com/user-attachments/assets/7e51047f-fd5d-4c4b-add0-4b5fd6412c98" />

<img width="1605" height="341" alt="image" src="https://github.com/user-attachments/assets/a4c6b832-493e-410a-b7f5-8ef981eb33cd" />

## Task 9: Conclusion
### Conclusion

### - Covered basic concepts of Active Directory and Windows Domains  
### - Serves as an introduction, more advanced topics exist. 

# Thankyou :)

















