# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Splunk Basics - Did you SIEM?
### Learn how to ingest and parse custom log data using Splunk.
<img width="1905" height="421" alt="image" src="https://github.com/user-attachments/assets/ab2f2d47-6887-489a-92fe-9a74c4e788a5" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/0d73da5f-9f34-4f40-a742-8889ecebd55f" />

### Ransom Alert in Wareville
### As Christmas approaches in Wareville, TBFC is busy with preparations when the SOC dashboard suddenly triggers a critical alert
### A ransom message appears on the system, indicating a potential cyber attack disrupting operations
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/635eca51-1bfb-4e1f-a95d-436045254fcf" />

### King Malhare’s Attack
### The ransom message is from King Malhare, who launched an attack using his Bandit Bunnies to turn Christmas into EAST-mas
### With McSkidy missing and systems compromised, the situation becomes critical for TBFC
### We will use Splunk to investigate how the ransomware entered the system and stop the attack before Christmas is ruined

### Learning Objectives

### We will learn how to ingest and analyze custom log data using Splunk
### We will create and apply custom field extractions for better data visibility
### We will use SPL (Search Processing Language) to filter and refine search results

## Task 2 Log Analysis with Splunk
### Start the machine
<img width="701" height="281" alt="image" src="https://github.com/user-attachments/assets/febbccb9-26a2-407f-a12b-1e7e9b6a1ffa" />

### Exploring the Logs in Splunk
### We will begin by accessing the pre-ingested data available in the Splunk instance for investigation
### From the Splunk dashboard, we will navigate to the `Search & Reporting` section on the left panel to start analyzing the logs
<img width="959" height="867" alt="image" src="https://github.com/user-attachments/assets/d284cc08-01e0-4b0d-a298-f5a2e4b46cbe" />

### What is the attacker IP found attacking and compromising the web server?
### We will search for all logs by entering "sourcetype="Web_traffic" in the search bar
<img width="959" height="867" alt="image" src="https://github.com/user-attachments/assets/6589b085-7664-4c72-8182-00d67779ec30" />

### We found the Attacker ip: 198.51.100.55
<img width="752" height="656" alt="image" src="https://github.com/user-attachments/assets/6a68e5f8-6d00-4b7c-ba52-2c288e426bb5" />

### Which day was the peak traffic in the logs? (Format: YYYY-MM-DD)
### add | timechart span=1d count to sort the peak traffic in the web server
### This command takes time chart of timespan of 1 day in counts 
<img width="958" height="847" alt="image" src="https://github.com/user-attachments/assets/e4e05346-14ec-4194-913e-c155df30f5fd" />

### Date is 2025-10-12
### What is the count of Havij user_agent events found in the logs?
### In the user_agent="Havji/1.17 (Automated SQL Injection)"
<img width="957" height="868" alt="image" src="https://github.com/user-attachments/assets/098e2455-2263-4a4b-9672-83bc0c123704" />

### 993 Events

### How many path traversal attempts to access sensitive files on the server were observed?
### sourcetype="web_traffic" path="*..\/
### This command sort by web traffic and path which has ../ 
### ../ Indicator of directory traversal.
<img width="959" height="865" alt="image" src="https://github.com/user-attachments/assets/b1b97697-d958-4d71-a86e-e4285bafef60" />

### 658 Events
### Examine the firewall logs. How many bytes were transferred to the C2 server IP from the compromised web server?
### Enter this in search Index sourcetype="firewall_logs" dest_ip=198.51.100.55
### This command sort the logs of destination Ip 198.51.100.55 through firewall
### stats sum(bytes_transfereed)
### This stats the sum of bytes transfereed between C2 Ip and compromised web server
<img width="959" height="868" alt="image" src="https://github.com/user-attachments/assets/c6518dcd-95ef-48c1-b9b8-efaee10669bb" />

### The sum is 126167
<img width="956" height="870" alt="image" src="https://github.com/user-attachments/assets/34914b03-13c3-4dd6-a59e-092eb781d472" />

<img width="1623" height="866" alt="image" src="https://github.com/user-attachments/assets/2ebf7921-93ff-4ef7-920d-d536ef6c60c0" />

### Congratulations !!! We have Succesfully Completed the Room
<img width="1908" height="432" alt="image" src="https://github.com/user-attachments/assets/0d6a13a4-5a6d-4cd1-96a7-5c756583834d" />





