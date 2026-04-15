# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1902" height="420" alt="image" src="https://github.com/user-attachments/assets/59acbc62-c637-4ae4-b897-697a1d56b9fc" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/e13114a6-ba94-452b-8905-a71b182b6ae7" />

### McSkidy’s kidnapping has weakened Wareville’s defenses, putting Christmas at risk as the TBFC team begins investigating.
### TBFC’s first lead is tbfc-web01, a Linux server handling Christmas wishlists.
### The server may hold clues about McSkidy’s last actions and King Malhare’s EASTMAS plan.
### Click start attack machine
<img width="906" height="350" alt="image" src="https://github.com/user-attachments/assets/b703783c-5d7e-4faa-82d2-a0595dd97fdb" />

<img width="980" height="618" alt="image" src="https://github.com/user-attachments/assets/4750e590-f190-4792-827f-afb0daafc789" />


### Learning Objectives
### Understand Linux CLI basics and its use in personal and IT tasks
### Apply these skills to investigate the Christmas mystery and connect to the machine

## Task 2 Linux CLI
### Linux CLI Introduction
### Linux provides a powerful command-line interface (CLI) to manage the system using typed commands
### It becomes easier with practice and can even be preferred over graphical interfaces
### Running Basic Linux CLI Commands
### First, we will  type `echo "Hello World!"` and it simply prints the text back on the screen
### Then we will use `ls` to list all files in the current directory, including McSkidy’s files
### After that, we will run `cat README.txt` to open and display the contents of the file
<img width="980" height="492" alt="image" src="https://github.com/user-attachments/assets/24384dc7-7956-4000-a75a-257c18d3d589" />

### It looks like McSkidy left behind a security guide before being kidnapped, which could help us
### We will confirm our location using `pwd`, starting from McSkidy’s home directory
### We will move into the Guides folder using `cd Guides`, now at `/home/mcskidy/Guides`
### Then we will run `ls`, but the directory is empty, even though we expected useful files
### Files starting with a dot (.) are hidden, so we will first reveal them using `ls -la` to see everything including hidden files and details like permissions and ownership
### Now we can identify the hidden guide file, then we will read it using `cat .guide.txt`, making sure to include the dot in the filename
<img width="840" height="543" alt="image" src="https://github.com/user-attachments/assets/4cd00a9a-7311-4dfb-ad49-2743eabe177f" />

### We have found the flag THM{Learning-linux-cli}

### Grepping the Logs
### We will navigate to the `/var/log/` directory using `cd /var/log` and list its contents with `ls` to explore available log files
### Since logs are large, we will use `grep` instead of `cat` to efficiently search for specific events
### Now we will run `grep "Failed password" auth.log` to find failed login attempts inside the authentication log
<img width="849" height="772" alt="image" src="https://github.com/user-attachments/assets/de77429f-1a71-4408-96f4-e09409ee0acf" />
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/3a54883a-539b-4571-9bd8-a82381ca7e49" />

### Finding the Files
### We notice multiple failed logins on the "socmas" account from the HopSec location, suggesting an attempted breach of SOC-mas
### Now we will use the `find` command to search for suspicious files related to “eggs” (Eggsploit/Eggshell) inside the home directory
### We will run `find /home/socmas -name *egg*` to locate any files matching the pattern and investigate further
<img width="848" height="68" alt="image" src="https://github.com/user-attachments/assets/98db53f1-938f-4641-9c5e-8efb4a7ad363" />

### Analyzing the Eggstrike
### We will inspect the suspicious file `eggstrike.sh`, which is a shell script that may contain automated CLI commands
### Shell scripts are commonly used for automation in IT, but attackers can also use them to run malicious actions
### Now we will display its contents to understand what it does and investigate any potential threat
<img width="900" height="374" alt="image" src="https://github.com/user-attachments/assets/5f806124-5e90-45a2-849c-0fac86918c96" />

### Understanding the Eggstrike Script
### We will ignore lines starting with `#` since they are just comments and not executed commands
### The command `cat wishlist.txt | sort | uniq` processes the wishlist and extracts unique items, then saves the output to `/tmp/dump.txt`
### Next, `rm wishlist.txt` deletes the original wishlist file containing Christmas wishes
### Finally, `mv eastmas.txt wishlist.txt` replaces the original wishlist with a modified file, suggesting possible malicious manipulation
<img width="1616" height="476" alt="image" src="https://github.com/user-attachments/assets/7a97bc97-347e-4257-91a4-a9baf1289363" />

### We have found the flag THM{sir-carrotbane-attacks}

### Sir Carrotbane Attacks
<img width="1064" height="1062" alt="image" src="https://github.com/user-attachments/assets/b5e18cfc-5e40-44f6-91dd-f7659caae81a" />

### We now confirm the server has been breached, and the original Christmas wishlist has been replaced with an EASTMAS version
### Although we still have no direct clue about McSkidy’s location, we can clearly see evidence of attacker activity on the system
### We will verify this by opening `http://MACHINE_IP:8080` in the Firefox browser on the VM to observe the changes made

### System Utilities and Root Access
### We will use basic system commands like `uptime`, `ip addr`, and `ps aux` to understand system status, network info, and running processes
### Sensitive user data like `/etc/shadow` contains hashed passwords and can only be accessed with root privileges
### We will switch to the root user using `sudo su`, since root has full control over the system and is often targeted by attackers
### We can confirm our current user at any time using `whoami`, and return to the normal user with `exit`
<img width="968" height="676" alt="image" src="https://github.com/user-attachments/assets/d5d72106-902e-489f-9a60-124e36a296f9" />

### Bash History
### We will explore Bash history, which stores every command previously executed by the user in a hidden log file
### First, we will use the `history` command to view recently run commands directly in the terminal
### Then we will check the actual stored file using `cat .bash_history` to look for any traces left by Sir Carrotbane or the attackers
<img width="966" height="556" alt="image" src="https://github.com/user-attachments/assets/45099324-df71-4305-afbf-7ba2989b92dd" />

### We found another flag THM{until-we-meet-again}
### Objective
<img width="1610" height="855" alt="image" src="https://github.com/user-attachments/assets/3117f5b8-1c59-47f7-b92d-3cdab2da2464" />

<img width="1603" height="315" alt="image" src="https://github.com/user-attachments/assets/a024c765-f3f0-45b7-b3c5-92613a6e74c3" />

### Congratulations !!! We have Successfuly Completed the Room
<img width="1902" height="567" alt="image" src="https://github.com/user-attachments/assets/cec914c4-3111-46b9-a0bf-0113127dd8f5" />








