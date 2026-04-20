# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Today, We are going to discover how to scan network ports and uncover what is hidden behind them.
<img width="1907" height="427" alt="image" src="https://github.com/user-attachments/assets/6ce1fc10-0e75-4383-9a49-c4bc9b5c9cc0" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/3595d36b-3a81-4f7b-afcc-20329cc388ba" />

### We are going to assume HopSec has breached the TBFC QA environment and locked access to tbfc-devqa01, stopping all SOC-mas pipeline testing.  
### We suppose the server is being altered into a malicious EAST-mas node, making recovery urgent.
### • We are going to assume HopSec has taken unauthorized control of the QA environment.  
### • We suppose system operations are frozen due to the breach.  
### • We do this where we must trace HopSec activity and regain access to tbfc-devqa01.  
### • We are going to assume we must check all ports and entry points to restore the server before full takeover.  
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/ddae5c99-4d6a-4af8-af6f-c0c0e5163cb2" />

### Learning Objectives
### • Learn the basics of network service discovery with Nmap
### • Learn core network protocols and concepts along the way
### • Apply your knowledge to find a way back into the server

### Start the Attack and Target machine
<img width="919" height="623" alt="image" src="https://github.com/user-attachments/assets/5633e18e-e8bb-499f-9772-ae0cdbeff304" />


## Task 2 Discover Network Services
### We will perform reconnaissance on the QA server to identify exposed services and possible entry points.
### We will analyze open ports and use the findings to progress toward gaining system access.

### • We will target **tbfc-devqa01 (10.49.145.119)** for enumeration  
### • We will scan for open ports such as 22 (SSH) and 80 (HTTP)  
### • We will investigate running services to identify potential vulnerabilities  
### • We will exploit exposed services to gain initial access to the system  
### • We will collect **3 keys** in `KEYNAME:KEY` format 

### Simple form of Scanning
### Nmap is a widely used tool for scanning open ports and identifying exposed services on a target system.
### Run a basic Nmap scan from your attacking machine to quickly discover accessible ports and entry points.
<img width="922" height="475" alt="image" src="https://github.com/user-attachments/assets/70a62c29-e529-4e28-a1bc-1dde2b09a63b" />

### We will run a basic port scan to check the most commonly used 1000 ports and identify any exposed services on the target machine.
### The results show SSH and HTTP as the only open services, meaning we can either attempt remote login via SSH or access the web server directly.
### • We will confirm open services on the top 1000 scanned ports  
### • We will identify SSH access (port 22) as a potential entry point if credentials are available  
### • We will access the web application via http://10.49.145.119 from the AttackBox to continue enumeration
<img width="949" height="892" alt="image" src="https://github.com/user-attachments/assets/7166499a-afc0-4ebd-b885-7df0b29ea386" />


### Scanning all ranges
### We notice the website is defaced by bad bunnies, so we expand our scan to all 65535 ports using -p- along with --script=banner to uncover hidden services.
### This helps us move beyond the limited 1000-port scan and gather service banners that may reveal useful information for further exploitation.
### • We scan the full port range (65535) to ensure no hidden services are missed  
### • We use banner grabbing to identify running services and their versions  
### Banner name-Pwned by HopSec
<img width="801" height="634" alt="image" src="https://github.com/user-attachments/assets/ac7aec6e-fcf7-4cae-a740-6d70a8fa7e26" />


### We will identify additional exposed services, including an FTP server and a custom TBFC application, which may provide new entry points for access.
### Since FTP can run on non-standard ports (e.g., 21212 instead of 21), we will attempt to connect and test anonymous login using the ftp command.
### Found the flag KEY1:3aster_
<img width="810" height="546" alt="image" src="https://github.com/user-attachments/assets/a849d203-a6a3-4e19-9211-2766232e6ce5" />


### We will move on to the custom TBFC application running on port 25251 since the FTP server does not reveal any further useful information.
### As this is not a standard service like HTTP or FTP, we will use Netcat (nc) to interact directly with the port and test its response.
### • We will shift our focus to the TBFC application on port 25251 for further investigation  
### • We will use Netcat (nc) since standard browsers and clients cannot communicate with this custom service  
### Found the second flag KEY2:15_th3_
<img width="809" height="628" alt="image" src="https://github.com/user-attachments/assets/5b390bde-79e4-485f-a430-377014a0d734" />


### We will explore UDP ports as well, since earlier we only scanned TCP ports and important services might be hidden in UDP space too.
### By using a UDP scan with the -sU flag, we can identify additional services such as DNS that may contain useful information for further progress.
### • We will extend our scan to UDP ports to avoid missing hidden services  
### • We will discover an open DNS service on port 53, which is commonly used for domain resolution  
### • We will use DNS queries (dig) to interact with the service and check if it reveals the final key  
<img width="804" height="365" alt="image" src="https://github.com/user-attachments/assets/f62fb66b-424f-4521-a7b0-3c1005ee71d2" />

### Found the third flag "KEY3:n3w_xm45"
<img width="794" height="109" alt="image" src="https://github.com/user-attachments/assets/b6bfe675-5d87-4ff2-a844-1c38a41e571b" />


### On-Host Service Discovery
### We will now use the three collected keys to access the tbfc-devqa01 QA server admin panel and proceed with removing the bad bunnies from the system.
### • We will access the admin panel by visiting http://MACHINE_IP from the AttackBox  
### • We will combine the previously discovered keys to authenticate into the secret admin console  
<img width="902" height="441" alt="image" src="https://github.com/user-attachments/assets/2620154f-66b9-4775-845f-a08420503563" />

### We have Entered the keys
<img width="560" height="247" alt="image" src="https://github.com/user-attachments/assets/b4b46f2c-899f-4f75-b26e-fffa89073806" />

### Lets Access to the terminal
<img width="568" height="390" alt="image" src="https://github.com/user-attachments/assets/6e68f3b6-7ae2-4d75-ba50-5cba407190f1" />

### We will now use the Secret Admin Console to directly inspect the system instead of performing external port scans.
### By listing listening ports with ss -tunlp, we can identify active services and understand what is exposed internally versus externally.
### • We will use system commands (ss -tunlp or netstat) to list all listening ports on the host  
### • We will identify services bound to 0.0.0.0 (externally accessible) and 127.0.0.1 (locally accessible only)  
<img width="949" height="839" alt="image" src="https://github.com/user-attachments/assets/7094bfcc-605a-4fa3-9c70-bd3cbd4dba02" />

### We will focus on the MySQL service running on port 3306, as it often stores critical application data that may help us progress further.
### Since we already have host access, we can interact with the database locally, where authentication may not be required.
### • We will inspect the MySQL service running on the default port 3306  
### • We will take advantage of possible localhost trust to attempt unauthenticated access  

<img width="945" height="323" alt="image" src="https://github.com/user-attachments/assets/aa7c1693-694a-4329-9cc5-52226c64be8c" />

### We have captured the final flag  THM{4ll_s3rvice5_d1sc0vered}
### Answers of the path
<img width="1623" height="859" alt="image" src="https://github.com/user-attachments/assets/d5f9034d-37a4-4165-affd-856d8ba9c579" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1242" height="615" alt="image" src="https://github.com/user-attachments/assets/e5c25160-7e46-4046-8a1e-b56a9d206e36" />

