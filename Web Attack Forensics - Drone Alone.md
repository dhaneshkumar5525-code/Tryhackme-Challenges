# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Web Attack Forensics - Drone Alone
### Today, We are going to learn and explore web attack forensics using Splunk.
<img width="1772" height="423" alt="image" src="https://github.com/user-attachments/assets/3aed263a-4453-42f8-8aed-6d356e40ccf8" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/9493dd8b-1a94-4559-bdcf-d1899c5fe228" />

### Incident Investigation with Splunk  

### We are going to investigate suspicious long HTTP requests containing Base64 chunks, as this helps identify possible web server exploitation, resulting this shows signs of compromise.  
### We are going to use Splunk to analyze Apache logs and Sysmon telemetry, as this helps detect compromised hosts, decode payloads, and determine the attack scope accordingly.  

### • Splunk raised an alert: Apache spawned an unusual process  
### • Long HTTP requests contain Base64 payloads with hidden shell code  
### • Some requests allow the web server to execute malicious commands  
### • We will pivot between Apache logs and Sysmon host-level telemetry

### Learning Objectives  
### • Detect and analyze malicious web activity through Apache access and error logs  
### • Investigate OS-level attacker actions using Sysmon data  
### • Identify and decode suspicious or obfuscated attacker payloads  
### • Reconstruct the full attack chain using Splunk for Blue Team investigation  

### Turn on both machines
### Attacker machine ip 10.48.132.21 and Target machine ip 10.48.166.189
<img width="1099" height="659" alt="image" src="https://github.com/user-attachments/assets/a4ac4ea6-12bd-4289-8cce-cbf845d464d4" />

### Connnet the splunk through Target machine
### Open the browser and enter http://10.48.166.189:8000 to access the machine
<img width="1022" height="904" alt="image" src="https://github.com/user-attachments/assets/0ee06dfd-5412-414c-a212-db63c7299fd8" />

### Splunk dashboard
<img width="1298" height="894" alt="image" src="https://github.com/user-attachments/assets/9cc6c011-e734-425b-913f-27a82f47a54e" />

## Detect Suspicious Web Commands
### Navigate to the search and reporting
### We are going to check for `cmd.exe`, `PowerShell`, and `Invoke-Expression` in web logs accordingly.  
### • Search suspicious HTTP requests  
### • Look for `cmd.exe`, `PowerShell`, and `Invoke-Expression`  
### • These show command injection attempts  
### • The target is the vulnerable `hello.bat` script 
### Here is the command
### index=windows_apache_access (cmd.exe OR powershell OR "powershell.exe" OR "Invoke-Expression") | table _time host clientip uri_path uri_query status

### Command Query Explanation  
### • `index=windows_apache_access` → Searches Apache web server logs from Windows systems  
### • `(cmd.exe OR powershell OR "powershell.exe" OR "Invoke-Expression")` → Looks for suspicious command keywords that may show attacker activity  
### • `cmd.exe` → Checks for Command Prompt execution attempts  
### • `powershell / powershell.exe` → Detects PowerShell usage often used in attacks  
### • `"Invoke-Expression"` → Identifies PowerShell command execution, often used in hidden attacks  
### • `| table _time host clientip uri_path uri_query status` → Shows important details like time, host, attacker IP, path, query, and status code  

<img width="1920" height="537" alt="image" src="https://github.com/user-attachments/assets/2f58a8f1-97b3-4614-b426-3f689d2c0e51" />

### Make sure selecting the time range to All Time
### We can observe attacker trying to run hello.bat in cmd with encoded powershell.exe
### lets decode  the base64 encoded powershell command
### VABoAGkAcwAgAGkAcwAgAG4AbwB3ACAATQBpAG4AZQAhACAATQBVAEEASABBAEEASABBAEEA
<img width="1540" height="744" alt="image" src="https://github.com/user-attachments/assets/774a0d96-19ac-4f22-a8cf-a1086a191718" />

### The decoded message says “This is now Mine! MUAHAAHAA”

## Server-Side Errors or Command Execution in Apache Error Logs
### We are going to inspect web server error logs, as this helps us identify suspicious and malicious activity.  
### We will use the following query to detect errors and investigate possible attacker actions accordingly.
### index=windows_apache_error ("cmd.exe" OR "powershell" OR "Internal Server Error")
### Command Explanation  
### • `index=windows_apache_error` → Searches Apache error logs from Windows systems  
### • `("cmd.exe" OR "powershell" OR "Internal Server Error")` → Looks for suspicious errors related to command execution or server failures  
### • `cmd.exe` → Checks for Command Prompt execution attempts  
### • `powershell` → Detects PowerShell usage that may indicate attacker activity  
### • `Internal Server Error` → Identifies server errors that may happen during exploitation attempts  

### Before we are using the access logs, Now we are going to use error logs
<img width="1686" height="592" alt="image" src="https://github.com/user-attachments/assets/4e81e862-0967-4665-9e01-c881aea4cdb1" />

### change the view from list to raw
### We can observe the logs /cgi-bin/hello.bat?cmd=powershell ... is  as internal or external command 
### Which says the attack was unsuccessfull and the reason these logs are in apache_error

## Trace Suspicious Process Creation From Apache
### We are going to explore Sysmon logs, as this helps us identify malicious executable files spawned by the web server.  
### We will use the following Splunk query to detect suspicious process creation and investigate attacker activity accordingly.
### Command Explanation  
### • `index=windows_sysmon` → Searches Sysmon logs from Windows systems  
### • `ParentImage="*httpd.exe"` → Looks for processes where the parent process is `httpd.exe` (Apache web server)  
### • `httpd.exe` → Identifies processes started by the Apache server  
### • This helps detect malicious executables spawned through web exploitation  
### • Accordingly, we can trace attacker activity from the web server  

<img width="1688" height="884" alt="image" src="https://github.com/user-attachments/assets/703ce7d3-ff13-452d-9a68-88ddf1523312" />

### Here we can see the raw logs change the view to table
<img width="1404" height="448" alt="image" src="https://github.com/user-attachments/assets/d0f7a53a-54a8-49fd-976e-e209ed564caf" />

### Here we can see multiple logs which has image \windows\system32\cmd.exe and command line  Apache24\cgi-bin\hello.bat
## Important :

### Typically, Apache should only spawn worker threads, not system processes like cmd.exe or powershell.exe.
### If results show child processes such as:
### ParentImage = C:\Apache24\bin\httpd.exe
### Image        = C:\Windows\System32\cmd.exe
### It indicates a successful command injection where Apache executed a system command.

## Confirm Attacker Enumeration Activity
### We are going to identify what the discovered programs do, as this helps us understand attacker actions on the system.  
### We will use the following query to analyze the behavior of the suspicious executables accordingly.  
### index=windows_sysmon *cmd.exe* *whoami*
### Command Explanation  
### • `index=windows_sysmon` → Searches Sysmon logs from Windows systems  
### • `*cmd.exe*` → Looks for Command Prompt execution activity  
### • `*whoami*` → Searches for the `whoami` command used to check the current user  
### • This helps identify attacker commands executed on the system  
### • Accordingly, we can understand what actions were performed after exploitation
<img width="1685" height="655" alt="image" src="https://github.com/user-attachments/assets/323e1928-a0cf-47c0-8cf6-a44a36bdaa0f" />

### Here we can observe different image Apache24/cgi-bin/whoami.exe and the command line is whoami
<img width="1237" height="371" alt="image" src="https://github.com/user-attachments/assets/6ebd87d3-b30e-409d-a630-2df0d3051222" />

### Finding these events confirms the attacker’s post-exploitation reconnaissance, showing that the injected command was executed on the host.

### Identify Base64-Encoded PowerShell Payloads
### We are going to find all successfully encoded commands, as this helps us identify hidden attacker payloads.  
### We will use the following Splunk query to search for encoded strings and analyze malicious activity accordingly.  
### index=windows_sysmon Image="*powershell.exe" (CommandLine="*enc*" OR CommandLine="*-EncodedCommand*" OR CommandLine="*Base64*")
### Command Explanation  
### • `index=windows_sysmon` → Searches Sysmon logs from Windows systems  
### • `Image="*powershell.exe"` → Looks for PowerShell process execution  
### • `CommandLine="*enc*"` → Detects short form of encoded command usage  
### • `CommandLine="*-EncodedCommand*"` → Finds PowerShell commands using full encoded command option  
### • `CommandLine="*Base64*"` → Searches for Base64 encoded payloads  
### • This helps identify hidden or obfuscated attacker commands  
<img width="1690" height="359" alt="image" src="https://github.com/user-attachments/assets/fee1321f-57db-41b4-9999-76cac2e4e7f9" />

### No results found !
### If your defences are correctly configured, this query should return no results
### Meaning the encoded payload (such as the “Muahahaha” message) never ran.

### 1)What is the reconnaissance executable file name?
### Run these query index=windows_sysmon *cmd.exe* *whoami*
<img width="1237" height="371" alt="image" src="https://github.com/user-attachments/assets/6ebd87d3-b30e-409d-a630-2df0d3051222" />

### Scroll down to see original file name in the fields
<img width="1137" height="400" alt="image" src="https://github.com/user-attachments/assets/5c61bb78-39b4-4adc-bfff-1703236315e4" />

### Whoami.exe

### What executable did the attacker attempt to run through the command injection?
### We can see the executable attempt in this image
<img width="1920" height="537" alt="image" src="https://github.com/user-attachments/assets/2f58a8f1-97b3-4614-b426-3f689d2c0e51" />

### Powershell.exe
### Answers of the Room
<img width="1618" height="354" alt="image" src="https://github.com/user-attachments/assets/260c9a78-ed30-4e24-bbe2-9cb29b6bc486" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1731" height="427" alt="image" src="https://github.com/user-attachments/assets/671e409f-8c2b-44e4-8253-b0ecc11937ea" />














































































