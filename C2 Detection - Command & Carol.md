# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1676" height="420" alt="image" src="https://github.com/user-attachments/assets/f8964979-ec49-41ac-af1c-0083bbf950dc" />

### C2 Detection - Command & Carol  
### Today, we are going to learn how to analyze a large PCAP and extract valuable information.
## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/3fe25139-84c1-4910-bc74-3ea5d56e13d3" />

### We are going to investigate potential Command and Control (C2) activity, as TBFC suspects attackers may still be communicating with compromised systems.  
### To speed up the investigation, we will convert PCAP data into Zeek logs and use RITA (Real Intelligence Threat Analytics) to identify suspicious network behavior accordingly.  
### • TBFC is monitoring for signs of Command and Control traffic  
### • Large amounts of network traffic make manual analysis difficult  
### • Zeek converts PCAP files into structured network logs  
### • RITA analyzes Zeek logs to detect suspicious communication patterns  
### • Accordingly, RITA helps identify compromised hosts and potential attacker activity more efficiently  

### Learning Objectives  

### • Convert a PCAP file into Zeek logs  
### • Use RITA to analyze Zeek log data  
### • Analyze and interpret RITA findings and results  

## Task 2 Detecting C2 with RITA
<img width="1611" height="766" alt="image" src="https://github.com/user-attachments/assets/55f28ab8-880b-4456-a316-2f1c63f5c13c" />

### What is Zeek?  
### Zeek is an open-source Network Security Monitoring (NSM) tool that observes network traffic and converts it into structured logs for analysis.  
### Unlike firewalls or IDS/IPS solutions, Zeek does not block traffic; it focuses on monitoring, analyzing, and enriching network data accordingly.  
### • Zeek accepts traffic from SPAN ports, network taps, or PCAP files  
### • It analyzes network activity and generates structured log files 

### Turn on the target machine
<img width="996" height="623" alt="image" src="https://github.com/user-attachments/assets/5f424ef0-d893-444e-9e10-2ebec8fc6777" />

### Use listout pcaps command to listout all the pcap files 
<img width="908" height="488" alt="image" src="https://github.com/user-attachments/assets/61be8886-1900-4aee-a1cc-3015bc3195a9" />

### rita_challenge.pcap. But rita cannot read pcap files on there own. Convert into the zeek files
### To convert enter the command 
### zeek readcap pcaps/rita_challenge.pcap zeek_logs/rita_challenge 
<img width="908" height="562" alt="image" src="https://github.com/user-attachments/assets/c3c3bcc2-b407-4374-ae82-7fd98dd744d1" />

### enter ls zeek_logs/rita_challenge/
<img width="910" height="219" alt="image" src="https://github.com/user-attachments/assets/d9ad2b46-9122-4ba5-8c9e-467a7ac8256d" />

### We can import all the pcap files into the database
### rita import --logs zeek _logs/rita_challenge/database rita_challenge
<img width="906" height="204" alt="image" src="https://github.com/user-attachments/assets/96f56c54-5262-4258-b46c-90c85d99d62d" />

### Once the import is completed we will see the success message 
<img width="905" height="790" alt="image" src="https://github.com/user-attachments/assets/579f0827-a05d-4993-bc2b-3ae4b3cf99dd" />

### To view the data enter rita view rita_challenge (database name)
<img width="908" height="729" alt="image" src="https://github.com/user-attachments/assets/031448f6-d488-4cc1-9b24-016a1c566650" />

### Now database has opened in rita view  
<img width="1919" height="801" alt="image" src="https://github.com/user-attachments/assets/dfb7b5e6-a886-447e-ac95-82b348a73645" />

### Question 1 How many hosts are communicating with malhare.net?
<img width="1601" height="334" alt="image" src="https://github.com/user-attachments/assets/12056faf-fc3c-4ded-b565-e23da9958f3c" />
<img width="1600" height="322" alt="image" src="https://github.com/user-attachments/assets/3b87125c-fdb7-4b8c-85ad-8c9e70e97fe2" />

### There are 6 hosts are communicating with the malware.net

### Q2 Which Threat Modifier tells us the number of hosts communicating to a certain destination?
<img width="1702" height="522" alt="image" src="https://github.com/user-attachments/assets/cd492e3a-afd6-4ea3-a905-2aa7bfd2a805" />

### Q3 What is the highest number of connections to rabbithole.malhare.net?
### Select the connection and see the connection count on the right 
<img width="1913" height="531" alt="image" src="https://github.com/user-attachments/assets/8916c363-dce0-4e01-8658-e40c1d9d0ce1" />

###  The highest connection count is 40

### Q3 Which search filter would you use to search for all entries that communicate to rabbithole.malhare.net with a beacon score greater than 70% and sorted by connection duration (descending)?
### Lets learn about the filter > Go the search section and enter ? to see the filter commands
<img width="1604" height="666" alt="image" src="https://github.com/user-attachments/assets/b291707d-f661-4998-b57c-099717889daa" />

###  dst:rabbithole.malhare.net beacon:>=70 sort:duration-desc
<img width="1920" height="784" alt="image" src="https://github.com/user-attachments/assets/43e73e1f-837d-48b3-adc4-67181b0cb328" />

### Q4 Which port did the host 10.0.0.13 use to connect to rabbithole.malhare.net?
### Selet the connection and we can see the connection port in the right side details
<img width="1920" height="699" alt="image" src="https://github.com/user-attachments/assets/fc5e31f1-f807-4bb3-bfe5-f2d61b9bdf0a" />

### Answer : port80

### Answers for the room
<img width="1621" height="771" alt="image" src="https://github.com/user-attachments/assets/1b425057-3370-4262-910b-b7db9795780c" />

### Congratulations !!! We have Successfully Completed the room.
<img width="1679" height="449" alt="image" src="https://github.com/user-attachments/assets/70bb53f6-5c14-409b-97a8-c591e890a4a7" />










