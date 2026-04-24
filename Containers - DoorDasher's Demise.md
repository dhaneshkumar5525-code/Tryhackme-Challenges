# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Containers - DoorDasher's Demise
### Today, we are going to learn about container security.
<img width="1850" height="407" alt="image" src="https://github.com/user-attachments/assets/67da8542-2b92-4e69-9cc7-85b61cd66e06" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/ed3f5be3-733a-4ad4-af59-1ea55a9c0036" />

### DoorDasher Incident Investigation  

### We are going to investigate how King Malhare took control of DoorDasher, as we can observe the food delivery site was rebranded into Hopperoo, resulting this caused major chaos in Wareville.  
### We are going to use the monitoring pod to escape the container and escalate privileges, as we can observe this is the only remaining access to restore the system accordingly.  

### • DoorDasher is Wareville’s local food delivery platform and a favorite of TBFC workers  
### • As we can observe, King Malhare rebranded it as Hopperoo and changed all menu items  
### • Customers reported receiving Santa’s beard fragments instead of noodles, causing health and safety issues  
### • A security engineer created a restoration script but was locked out by Sir CarrotBaine before execution  

### Learning Objectives
### Learn how containers and Docker work, including images, layers, and the container engine
### Explore Docker runtime concepts (sockets, daemon API) and common container escape/privilege-escalation vectors
### Apply these skills to investigate image layers, escape a container, escalate privileges, and restore the DoorDasher service
### DO NOT order “Santa's Beard Pasta”

## Task 2 Container Security
### What Are Containers?
 
### We are going to understand containers, as we can observe modern applications face issues like installation problems, troubleshooting delays, and dependency conflicts, resulting this makes management difficult.  
### We are going to use containerisation as a solution, as we can observe it provides isolation by packaging applications with dependencies in one environment accordingly.  

### • Installation issues happen due to configuration differences in different environments  
### • As we can observe, troubleshooting becomes difficult when identifying if the issue is from the app or the environment  
### • Multiple versions of applications or dependencies can create conflicts  
### • Containerisation solves this by isolating applications with all required dependencies in a container  
### • Accordingly, containers are lightweight and make deployment faster and more reliable 

### Containers vs VMs
<img width="1766" height="1072" alt="image" src="https://github.com/user-attachments/assets/d8912020-d15b-4e46-81df-28b591075533" />

### • Virtual machines run on a hypervisor that manages multiple operating systems on one host  
### • As we can observe, VMs include a full guest OS, making them heavier but fully isolated  
### • Containers only isolate applications and dependencies while sharing the host OS kernel  
### • Resulting this, containers are lightweight and start much faster than VMs  
### • Accordingly, VMs suit different OS needs, while containers are better for scalable micro-services  

### Escape Attack & Sockets
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/5fa9172b-b7e3-457b-b419-116fc0e95b97" />

### We are going to understand container escape attacks, as container escapes allow code inside a container to gain access beyond its isolated environment, resulting this can compromise the host system.  
### We are going to analyze runtime sockets, as attackers can use them to communicate with the container daemon and exploit the host accordingly.  
### • A container escape allows execution on the host kernel or other containers  
### • Attackers may create privileged containers with more access, such as internet connectivity  
### • Containers use a client-server model where CLI tools send requests to the container daemon  

## Challenge
### We are going to investigate the Docker layers and restore Hopperoo back to DoorDasher, resulting this helps recover the original website.  
### We are going to follow the steps to complete the challenge, as this allows us to regain control of the system accordingly.  

### Turn both attack - 10.49.168.205 and target machine - 10.49.145.245
<img width="917" height="620" alt="image" src="https://github.com/user-attachments/assets/981b76e6-a5ba-4818-9f5b-892d87b513b7" />

### Access Points  
### We are going to start using the machine and check which Docker services are running, resulting this helps us identify available access points.  
<img width="946" height="832" alt="image" src="https://github.com/user-attachments/assets/7f135032-2dfa-4905-b11b-69af249d11f8" />

### docker ps
<img width="942" height="429" alt="image" src="https://github.com/user-attachments/assets/49be27a8-ee78-42f6-bf00-bf9efb4d28e5" />

### We are going to access the main service at `http://10.49.145.245:5001` and inspect the defaced Hopperoo website, resulting this helps us understand the compromised system.  
### We are going to explore the uptime-checker, as this may provide useful access for restoring DoorDasher accordingly.  
### docker exec -it uptime-checker sh
### We are logged in
### check the socket access by running: ls -la /var/run/docker.sock
<img width="920" height="180" alt="image" src="https://github.com/user-attachments/assets/b03f787f-b725-4430-b97b-409547a5a81e" />

### • Run `docker exec -it deployer bash` to access the container  
### • The deployer container is a privileged container  
### • Use `whoami` to verify the current logged-in user  
<img width="939" height="105" alt="image" src="https://github.com/user-attachments/assets/72fbafbe-cc75-4cd4-a6cf-fa625a551c6b" />

### We are going to run the `recovery_script` in the root directory using sudo, as this restores the application back to DoorDasher accordingly.  
<img width="932" height="314" alt="image" src="https://github.com/user-attachments/assets/cb663204-865e-46d5-a5d5-94d72bbad388" />

### Change the directory backwords cd.. and use ls command
<img width="941" height="226" alt="image" src="https://github.com/user-attachments/assets/25ba1be9-0a0d-41d1-938a-1aa45db2249e" />

### We have captured the flag THM{DOCKER_ESCAPE_SUCCESS}

### Bonus Question: There is a secret code contained within the news site running on port 5002; 
### this code also happens to be the password for the deployer user! They should definitely change their password. 
### Can you find it?
### Open the Browser and enter the Ip http://10.48.152.68:5001 and change the port to 5002
<img width="898" height="837" alt="image" src="https://github.com/user-attachments/assets/a5de52af-bb9c-48e1-b6ae-c0dbf2a4e61b" />

### Scroll down to find the secret message
<img width="897" height="826" alt="image" src="https://github.com/user-attachments/assets/e6c075d2-0735-47e6-9844-02e50c650072" />

### Observe the red highlighted text
<img width="897" height="826" alt="image" src="https://github.com/user-attachments/assets/529c12cd-5d66-4a74-b76e-fb8668dc1ce2" />

### We have found the message -DeployMaster2025!
### Congratulations !!! We have Successfully Completed the Room
<img width="1805" height="418" alt="image" src="https://github.com/user-attachments/assets/3cf32a24-7dae-4f42-8294-27c7ae749fe3" />

























