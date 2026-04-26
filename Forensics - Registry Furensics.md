# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Forensics - Registry Furensics
### Today, we are going learn what the Windows Registry is and how to investigate it.
<img width="1903" height="424" alt="image" src="https://github.com/user-attachments/assets/99a9653c-c096-425d-94f1-18756091ecc1" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/e5137718-c0e2-4c7d-806c-6ae591f53a85" />

### We are going to investigate the compromised system `dispatch-srv01`, as this helps us understand how the attack happened and recover control of the system.  
### We will focus on Windows Registry forensics, while other teams analyze logs, memory dumps, and file systems accordingly.  
### • TBFC is under attack and systems are showing unusual behavior  
### • `dispatch-srv01` is a critical server used for drone-based gift delivery during SOCMAS  
### • The system was compromised by King Malhare’s bunny bandits  
### • Different teams are handling logs, memory, and file system investigations  
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/298d9e9f-72d0-4298-b6a6-bdfb8c9e78f0" />

### Learning Objectives  
### • Understand what the Windows Registry is and what it contains  
### • Learn about Registry Hives and Root Keys  
### • Analyze Registry Hives using the Registry Editor tool  
### • Perform Registry Forensics using the Registry Explorer tool 

## Task 2 Investigate the Gifts Delivery Malfunctioning
### Windows Registry
### Your brain stores all the information that you need to function effectively. This includes:
### • It stores how the system should behave  
### • It keeps startup and login-related information  
### • It remembers user settings and preferences  
### • It tracks habits, configurations, and recent activity  
### • Accordingly, the Registry acts like the memory of the operating system
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/837f652b-3da4-496e-948b-306718033a40" />

### Just like the brain stores habits, behavior, and recent actions, Windows stores its system configurations in the Registry, which is divided into separate files called Hives accordingly.  

### • The human brain stores behavior, habits, dressing style, and recent past actions  
### • It works like a database storing the complete human configuration  
### • Similarly, Windows OS needs a brain to store all its configurations  
### • This brain is called the Windows Registry  
### • The Registry is made of separate files called Hives, each storing different configuration settings  

### We are going to look at the different Registry Hives, as each hive stores specific system and user configuration settings.  
### The table shows the hive names, the type of settings they store, and their location on the disk accordingly.  
<img width="1545" height="850" alt="image" src="https://github.com/user-attachments/assets/eb2ac0c9-59ad-4a66-b989-a9c4146425bd" />

<img width="1542" height="302" alt="image" src="https://github.com/user-attachments/assets/5c289e4d-d215-4603-b5f5-034c5ea5e4c8" />

### Note: The configuration settings stored in each hive listed above are just a few examples. Each hive stores more than these.

### The Windows OS has a built-in tool known as the Registry Editor, which allows you to view all the registry data available in these hives. 
### You can go ahead and open this tool by simply typing Registry Editor in your search bar.
### Win + R - regedit
<img width="455" height="266" alt="image" src="https://github.com/user-attachments/assets/2dcd661f-024b-4c69-a589-c60389f8dbb5" />

<img width="1425" height="435" alt="image" src="https://github.com/user-attachments/assets/f2250a96-d7fd-402a-85f0-e04cd177cfe6" />

### Why do we see folders like HKEY_LOCAL_MACHINE and HKEY_CURRENT_USER instead of SYSTEM, SECURITY, or SOFTWARE? Because Windows organizes Registry Hives into structured Root Keys instead of showing the Hive files directly.  

### Which Root Key contains which Registry Hive’s data? The table below answers this by mapping Registry Keys with their respective Registry Hives accordingly.  
### • Registry Editor shows Root Keys instead of direct Hive names  
### • SYSTEM, SECURITY, and SOFTWARE are Registry Hives, not Root Keys  
### • Windows groups these Hives under structured Root Keys  
### • This makes Registry navigation more organized and manageable  
### • The table below explains which Root Key stores which Hive data  

### Example 1: View Connected USB Devices
### How can we view USB device details? Open Registry Editor, go to this path, and we can see details like make, model, device ID, and unique device information accordingly.  
### • USB device information is stored inside the SYSTEM Hive  
### • The path used is `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR`  
<img width="2056" height="1068" alt="image" src="https://github.com/user-attachments/assets/82d15ae9-2177-4994-bec0-bf7fbb0aed6e" />

### Example 2: View Programs Run by the User
### Where does Windows store commands run using the Run dialog (Win + R)? The Registry stores this information in the `NTUSER.DAT` Hive under the path `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU`.  

### How can we view these commands? Open Registry Editor, navigate to this path, and we can see the list of commands typed by the user accordingly.  

### • Run dialog activity is stored inside the `NTUSER.DAT` Hive  
### • The path used is `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU`  
### • It records commands entered using `Win + R`  
### • This helps track programs executed by the user  
### • Accordingly, it is useful in forensic investigations  
<img width="2050" height="1076" alt="image" src="https://github.com/user-attachments/assets/1c463344-f38b-40c7-b97a-cd94093649c4" />

### We are going to understand Registry Forensics, as the Windows Registry stores important system information that helps in forensic investigations.  
### We will analyze registry data along with logs, memory dumps, and file system data to build the complete incident timeline accordingly.  
<img width="1543" height="844" alt="image" src="https://github.com/user-attachments/assets/fed3d0b3-d71d-43af-be35-3b2021f24994" />


<img width="1542" height="362" alt="image" src="https://github.com/user-attachments/assets/dee5d54a-d78e-4d68-ba13-27cc2ee6879c" />

### We are going to identify important Registry Keys, as these store useful evidence like recent activity, startup programs, installed apps, and system details.  

### Registry analysis is usually done offline because investigating directly on the target system may change evidence, and Registry Editor does not support opening offline hives accordingly.  

### • `UserAssist` stores recently accessed applications launched through GUI  
### • `TypedPaths` stores paths typed in the Explorer address bar  
### • `Run` stores startup programs that run during user login  
### • `RecentDocs` stores recently accessed files by the user  
### • Registry Editor cannot open offline hives and may show unreadable binary values  

## Practical 
### Lets dive into forensics
### Turn on the Target Machine
<img width="912" height="387" alt="image" src="https://github.com/user-attachments/assets/9424fdf7-9c53-4c81-9aff-f1cf920998ce" />

### We are inside the target machine
<img width="1682" height="974" alt="image" src="https://github.com/user-attachments/assets/ef08c27c-a7f1-441c-906e-fadc857624ca" />

### We are going to use Registry Explorer to analyze the Registry Hives from the compromised system dispatch-srv01, as this helps in forensic investigation.  
### The collected Registry Hives are available in C:\Users\Administrator\Desktop\Registry Hives for offline analysis accordingly. 

### Step 1: Launch Registry Explorer
<img width="1282" height="679" alt="image" src="https://github.com/user-attachments/assets/ba83982b-fdc7-4c14-b9b3-dc037c6484d0" />

### We will load the hive files by using the File option and selecting Load hive accordingly.  
### • Open Registry Explorer with an empty interface  
### • Click on the File menu at the top  
### • Select Load hive from the dropdown  

### Step 2: Load the Registry Hives
### • Open Registry Explorer with an empty interface  
### • Click on the File option from the top menu  
### • Select Load hive from the dropdown  
### Navigate to the path
<img width="1275" height="368" alt="image" src="https://github.com/user-attachments/assets/e8bcac57-0312-4c2c-a0e5-a821ddecdb89" />


### Step 3: Handling Dirty Hives
### We will ensure clean loading by selecting the hive file and using SHIFT + Open to include transaction logs accordingly.  
### • Navigate to `C:\Users\Administrator\Desktop\Registry Hives` in Load hives window  
### • Select the required hive file (example: SYSTEM)  
### • Hold SHIFT and click Open to load transaction logs  
### • This ensures a clean and consistent hive state  
### • Accordingly, it improves accuracy of forensic analysis
<img width="941" height="585" alt="image" src="https://github.com/user-attachments/assets/d3a4dc20-607a-48aa-9320-975fb5c78d1f" />

### Step 4: Investigating Registry Keys
### Navigate to: ROOT\ControlSet001\Control\ComputerName\ComputerName. 
### Or you can also just type "ComputerName" in the search bar to quickly locate the key
<img width="1920" height="873" alt="image" src="https://github.com/user-attachments/assets/b12e75e7-0123-4e8a-ae2a-e907a8cc0e5d" />

### 1)What application was installed on the dispatch-srv01 before the abnormal activity started?
### Tip: The table given in the Registry Forensics explanation is going to be your friend.
### Lets see registry table 
<img width="876" height="176" alt="image" src="https://github.com/user-attachments/assets/51703428-e5a2-42c1-8396-9e2296854bf8" />

### Load them registry explorer
<img width="938" height="584" alt="image" src="https://github.com/user-attachments/assets/8e301844-21a8-4e5a-a9e6-f298661ba8c7" />

### Shift + open 
<img width="668" height="809" alt="image" src="https://github.com/user-attachments/assets/875c3ba2-1946-49e2-a057-07e718a9dbd8" />

### Lets see applications that are uninstall according to the time stamp  21st October, 2025.
<img width="1522" height="948" alt="image" src="https://github.com/user-attachments/assets/3d32fdd0-e2c8-4ac4-86fa-2d83ce52fa97" />

### We can see the only application is uninstalled before the abnormal activity is "DroneManager Updater"
### 2)What is the full path where the user launched the application (found in question 1) from?
### Lets see registry table 
### HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist -It stores information on recently accessed applications launched via the GUI.
### Naviagate to search bar and search for UserAssist - According to the above path
### Scroll down to the list according to the timestamp
<img width="1522" height="917" alt="image" src="https://github.com/user-attachments/assets/5bd6b4ef-6a99-45d1-915c-e07e40038119" />

### We can see the path on 21th
### C:\Users\dispatch.admin\Downloads\DroneManager_Setup.exe
### 3)Which value was added by the application to maintain persistence on startup?
### Now, we are looking for the run key
<img width="1542" height="184" alt="image" src="https://github.com/user-attachments/assets/a5742704-67dd-4dd9-a193-dffa582e56f3" />

### Naviagate to search bar and search for Run - According to the above path
<img width="1526" height="940" alt="image" src="https://github.com/user-attachments/assets/b0975d0d-ff4a-4a10-a7fc-2b33d33e344e" />

### We can see the drone_helper in the above image and the path
### "C:\Program Files\DroneManager\dronehelper.exe" --background

### Answers for the Room
<img width="1616" height="457" alt="image" src="https://github.com/user-attachments/assets/d07da51b-2d69-486e-8e44-16739d6833ed" />

### Congratulations !!! We have Successfully Completed the Room
<img width="1776" height="438" alt="image" src="https://github.com/user-attachments/assets/8f0145b5-aadf-45c8-844f-a10e884aea36" />






