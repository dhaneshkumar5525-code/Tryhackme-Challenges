# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1170" height="658" alt="image" src="https://github.com/user-attachments/assets/3b9c5d01-9355-46c5-99d0-746942c96cab" />

## Challenge: Pyramid of Pain
<img width="1896" height="401" alt="image" src="https://github.com/user-attachments/assets/8b7e4018-1947-4338-a91c-cb7a174467be" />

## Task 1: Introduction:
### The Pyramid of Pain is a concept used to improve Cyber Threat Intelligence (CTI), threat hunting, and incident response.
### Understanding it helps Threat Hunters, Incident Responders, and SOC Analysts detect threats more effectively.
### It highlights the difficulty attackers face when defenders detect and respond to IOCs (Indicators of Compromise).

## Task 2: Hash Values (Trivial):
### MD5, SHA-1, and SHA-2 are common cryptographic hash algorithms used to identify files.
### Hashes help detect malware, but a single modified bit changes the hash entirely.
<img width="1100" height="366" alt="image" src="https://github.com/user-attachments/assets/1235c33b-d5f9-4f4c-aff6-93c9040d1805" />

### Tools like VirusTotal and Metadefender Cloud help lookup file hashes.
<img width="1844" height="813" alt="image" src="https://github.com/user-attachments/assets/6eb7baa9-ded7-4381-bdcc-808f444ef709" />

<img width="1546" height="694" alt="image" src="https://github.com/user-attachments/assets/bfc232b0-132f-4566-ac1b-ddf6ded6bf7c" />

### File hashes can be challenging for threat hunting when attackers create multiple variants.
### Filename for sample hash b8ef959a9176aef07fdca8705254a163b50b49a17217a4ff0107487f59d4a35d: Sales_Receipt 5606.xls
<img width="1920" height="971" alt="image" src="https://github.com/user-attachments/assets/6af7edfd-a680-4312-ba48-622149cb2ad5" />

### Here is the file name "Sales_Receipt 5606.xls"
<img width="1608" height="230" alt="image" src="https://github.com/user-attachments/assets/e671cf23-a127-40eb-a6f8-84abecd84d3d" />

## Task 3: IP Address (Easy):
### IP addresses identify devices on a network and can be blocked to stop attacks.
### Fast Flux is a DNS technique used by attackers to hide C2 servers behind changing IPs.
### Detecting malicious IPs helps defenders respond faster.
### First IP accessed by PID 1632: 50.87.136.52
<img width="1100" height="125" alt="image" src="https://github.com/user-attachments/assets/3eaa7aae-8872-4abd-b339-e2c9a1466afd" />

### First domain accessed by PID 1632: craftingalegacy.com
<img width="1610" height="342" alt="image" src="https://github.com/user-attachments/assets/bb75ad67-2c54-4d12-980d-2f14f97fdaaa" />


## Task 4: Domain Names (Simple):
### Domain names map IP addresses to readable text like evilcorp.com.
<img width="1100" height="310" alt="image" src="https://github.com/user-attachments/assets/63ca9a98-9ad2-4b00-b43f-42608b0761e4" />

### Attackers hide malicious domains using URL shorteners: bit.ly, goo.gl, tinyurl.com, etc.
### Previewing shortened URLs (adding +) shows the final destination website.
<img width="732" height="451" alt="image" src="https://github.com/user-attachments/assets/7ed49459-f7ce-4fbb-a421-99772527d5dc" />

### Malicious  Sodinokibi  C2 ( Command and Control Infrastructure)  domains:
<img width="1463" height="592" alt="image" src="https://github.com/user-attachments/assets/7a276075-41d7-4c93-8239-3d4d1dece4f8" />

### Any.run sandbox shows HTTP requests:
<img width="1100" height="264" alt="image" src="https://github.com/user-attachments/assets/ca15c67b-98fb-481b-af64-d5a131178c9e" />

### Connections from malware:
<img width="1100" height="268" alt="image" src="https://github.com/user-attachments/assets/40e90d14-4119-4baf-b829-70ce015205b8" />

### DNS Request:
<img width="1100" height="257" alt="image" src="https://github.com/user-attachments/assets/45433037-ac0d-4877-ae82-61aec97f0dca" />

### First suspicious domain: craftingalegacy.com, attack using Unicode domains is called a Punycode attack, and a shortened URL redirects to the actual malicious site.
<img width="1100" height="91" alt="image" src="https://github.com/user-attachments/assets/7fa189b8-0cfe-43f9-8968-729e7fefa796" />

<img width="1653" height="636" alt="image" src="https://github.com/user-attachments/assets/82007ef9-1bfc-4907-bf50-fb56d9518e40" />


## Task 5: Host Artifacts (Annoying):
### Host artifacts are traces malware leaves on systems, such as registry changes, dropped files, or suspicious processes.
### Suspicious process execution from Word: 
<img width="945" height="44" alt="image" src="https://github.com/user-attachments/assets/f32890be-0a7b-43bf-80f4-4945b43aeefb" />

### Suspicious events followed by opening a malicious application: 
<img width="1406" height="709" alt="image" src="https://github.com/user-attachments/assets/bfcd4969-8424-4427-9c1f-e85091cf45bb" />

### Example: regidle.exe POSTs to 96.126.101.6 on port 8080.
<img width="1203" height="267" alt="image" src="https://github.com/user-attachments/assets/1ad0ec48-341b-482e-b6fe-16f4c17caf93" />

### Dropped executable: G_jugk.exe.
<img width="1100" height="158" alt="image" src="https://github.com/user-attachments/assets/b5d57fd9-52dd-4150-9887-f66d23243341" />

### VirusTotal shows 11 vendors detected the host 96.126.101.6 as malicious.
<img width="1903" height="968" alt="image" src="https://github.com/user-attachments/assets/d982ed84-85e6-4e15-b6af-2fcb67e43068" />

<img width="1613" height="596" alt="image" src="https://github.com/user-attachments/assets/c9bc9724-f043-4033-92c4-2c23e744107a" />


## Task 6: Network Artifacts (Annoying):
### Network artifacts are signs of attacker activity visible in network traffic.
### User-Agent strings, URI patterns, and HTTP POSTs are key network artifacts.
### Tools like Wireshark/TShark and IDS logs help detect anomalies.
<img width="1100" height="151" alt="image" src="https://github.com/user-attachments/assets/dbfd33c6-ad52-49aa-b2c7-64b296307ddc" />

### Number of POST requests detected: 6.
### Example TShark command:
### tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap
<img width="1139" height="683" alt="image" src="https://github.com/user-attachments/assets/de42caa3-7e9f-40b1-a555-1be913d0a8f5" />

<img width="1100" height="275" alt="image" src="https://github.com/user-attachments/assets/de88b809-0a90-475c-9f24-d5752e9ddeda" />

### Browser in screenshot: Internet Explorer.
<img width="1506" height="583" alt="image" src="https://github.com/user-attachments/assets/05d9a84e-e1d4-475d-b016-be8ff1aa780d" />

<img width="1625" height="336" alt="image" src="https://github.com/user-attachments/assets/b6797ce3-260b-43ff-aa9c-bf8438027985" />


## Task 7: Tools (Challenging):
### Attackers’ Methods:
### Use utilities to create malicious macro documents (maldocs) for spearphishing.
### Deploy backdoors for C2 (Command and Control) infrastructure.-
### Build custom .EXE, .DLL files, payloads, or password crackers.

### Suspicious Sample:
- A Trojan dropped **Stealer.exe** in the Temp folder.
<img width="956" height="430" alt="image" src="https://github.com/user-attachments/assets/f4c89dfa-b561-45b9-bd5d-9f375da0abe8" />

- Execution of the suspicious binary can reveal malicious behavior.
<img width="822" height="48" alt="image" src="https://github.com/user-attachments/assets/ed3130e8-d690-44da-90d5-03cd0483790a" />

### Defensive Tools:
### Use **antivirus signatures, detection rules, and YARA rules** to detect malware.
### Resources for threat hunting and incident response:  
### [MalwareBazaar](https://bazaar.abuse.ch)  
### [Malshare](https://malshare.com)  

### Detection Rules:
### [SOC Prime Threat Detection Marketplace](https://www.socprime.com/) is a platform to find rules for the latest threats and CVEs.

### Fuzzy Hashing:
### Allows similarity analysis between files with minor differences.
### Example tool: [SSDeep](https://ssdeep-project.github.io/ssdeep/)  
### Helps identify variants of malware when exact hash values differ. 
<img width="822" height="48" alt="image" src="https://github.com/user-attachments/assets/b9b2e070-d30a-42f2-bc90-b8497eba1490" />

<img width="1627" height="346" alt="image" src="https://github.com/user-attachments/assets/9c80e1b1-e3f3-4e7c-a72d-d906cf424fe8" />


## Task 8: TTPs (Tough):
### TTPs = Tactics, Techniques, and Procedures from MITRE ATT&CK.
<img width="1920" height="1280" alt="image" src="https://github.com/user-attachments/assets/0100564f-04c7-45d5-b464-6366eb31d24a" />

### Detecting TTPs quickly minimizes attacker success.
### Example: Detecting Pass-the-Hash attacks stops lateral movement in Windows environments.
### Navigate to ATT&CK Matrix webpage. How many techniques fall under the Exfiltration category?
<img width="132" height="753" alt="image" src="https://github.com/user-attachments/assets/10f71441-60f2-42d6-85ce-1c63b039a1a1" />

### Techniques under Exfiltration: 9.
### Chimera is a China-based hacking group that has been active since 2018.
### What is the name of the commercial, remote access tool they use for C2 beacons and data exfiltration?
### Navigate to the exfiltration
<img width="140" height="411" alt="image" src="https://github.com/user-attachments/assets/47cc635d-781b-4d13-a6c2-ddc9c9b15c36" />

### Then Channels then to G0114
<img width="1060" height="71" alt="image" src="https://github.com/user-attachments/assets/38fe3c9d-e876-4cc9-a9a2-721bc2a39e09" />

<img width="1618" height="338" alt="image" src="https://github.com/user-attachments/assets/4705f483-f035-45c6-b660-643135a60690" />


## Task 9: Practical: The Pyramid of Pain:
### Complete the static site lab to apply knowledge of hashes, IPs, domains, host and network artifacts, tools, and TTPs.
### Click View Lab:
### Complete the static site. What is the flag?
<img width="994" height="825" alt="image" src="https://github.com/user-attachments/assets/65ac4517-751b-49e6-9c7e-315ac2af79e2" />

### Here is the Flag
<img width="421" height="194" alt="image" src="https://github.com/user-attachments/assets/5a8794e4-a0fd-4221-af68-1aed1e11c7c5" />

<img width="1614" height="363" alt="image" src="https://github.com/user-attachments/assets/95c4e0d8-ce23-48cd-8953-805be9675118" />



## Task 10: Applying the Pyramid of Pain
### Pick an APT group to research and find its indicators.  
### Determine what detection rules or approaches you can create.  
### Identify where the activity falls on the Pyramid of Pain.  
### Goal: cause maximum pain to the adversary using useful indicators. 
<img width="1605" height="218" alt="image" src="https://github.com/user-attachments/assets/c90558b6-7e79-4de9-831a-46e5be9cec60" />


## Congratulaion !!! We have Completed the Room.
<img width="1897" height="547" alt="image" src="https://github.com/user-attachments/assets/b5f500ef-c345-4d39-911b-93ac16a5379c" />



