# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Today, we are going to learn about ICS/Modbus - Claus for Concern
<img width="1354" height="426" alt="image" src="https://github.com/user-attachments/assets/13ba4606-64f0-4cbe-b50d-3e195a39c37b" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/05516bb0-ed0b-48ae-8dd8-b8d9f12c96c6" />

### Incident Overview  
### We are going to investigate a strange delivery system issue, as Christmas presents are being replaced with chocolate eggs and Easter-themed items despite the system reporting normal operations.  
### We will analyze the logistics and delivery systems to determine how the items are being altered and identify the cause accordingly.  
### • TBFC is experiencing major disruptions during its busiest shipping period  
### • Customers are receiving chocolate eggs and bunny-themed items instead of their ordered gifts  
### • Delivery drones are successfully completing deliveries, but the contents are incorrect  

### Then, on one of the monitoring screens, a message flashes for just a second before disappearing:
<img width="1498" height="97" alt="image" src="https://github.com/user-attachments/assets/94a7b455-2b0c-4ac8-b39b-61ba32e3883d" />

### We are going to investigate the TBFC Drone Delivery System, as attackers have compromised the drone fleet and manipulated deliveries.  
### We will uncover how the attack was performed and restore normal Christmas deliveries accordingly.  
### • Drone control systems have been compromised  
### • Sensor data and inventory selections are being manipulated  
### • Attackers are hiding evidence of their actions  

### A Mysterious Discovery
### As you walk through the warehouse control room, something catches your eye—a crumpled piece of paper on the floor near the PLC terminal. It looks like someone dropped it in a hurry.
### You pick it up and unfold it. The handwriting is hurried, almost frantic:
<img width="622" height="849" alt="image" src="https://github.com/user-attachments/assets/a9932fee-b2f8-4241-bca7-1acc82aeb205" />

<img width="620" height="492" alt="image" src="https://github.com/user-attachments/assets/d3690ceb-0e0e-4dcc-9d41-baccf857f005" />

### Learning Objectives  
### • Understand how SCADA systems monitor industrial processes  
### • Learn the role of PLCs in automation and control  
### • Understand how the Modbus protocol enables device communication 

## Task 2 SCADA (Supervisory Control and Data Acquisition)
### What is SCADA?  
### What is a SCADA system? SCADA acts as the command center of industrial operations, monitoring processes, collecting data, and sending commands to machines.  
### • Sensors & Actuators → Sensors collect real-world data, while actuators perform physical actions like moving motors or robotic arms  
### • PLCs (Programmable Logic Controllers) → Execute automation logic, process sensor data, and control actuators  
### • Monitoring Systems → Dashboards, CCTV cameras, and alarm panels used to observe operations in real time  
### • Historians → Databases that store operational data for analysis and incident investigations  
### • Accordingly, SCADA acts as the central system that coordinates and manages industrial processes 

### SCADA in the Drone Delivery System  

### We are going to investigate how the SCADA system controls TBFC's drone deliveries, as attackers have manipulated its functions to sabotage Christmas operations.  
### We will identify the compromised components and understand why SCADA systems are common targets for cyberattacks accordingly.  
### • Package Type Selection → Controls whether drones load gifts, chocolate eggs, or Easter baskets  
### • Delivery Zone Routing → Routes packages to Wareville districts, while Zone 10 sends items for disposal  
### • Visual Monitoring → CCTV feeds allow operators to observe warehouse activity in real time  
### The malware can directly interface with industrial control systems via the Modbus TCP protocol, enabling arbitrary reads and writes to device registers over TCP port 502.

<img width="1582" height="190" alt="image" src="https://github.com/user-attachments/assets/6336d16b-b7ca-43f3-8908-c11700bf34f1" />

## Task 3 PLC & Modbus Protocol
### What is a PLC? A PLC (Programmable Logic Controller) is an industrial computer designed to control machines and automate real-world processes with high reliability.  
### Why are PLCs important? They operate continuously, respond to events in real time, and communicate directly with industrial hardware accordingly.  
### • PLCs are built to withstand harsh environments such as heat, dust, moisture, and vibration  
### • They can run 24/7 for years without frequent reboots or downtime  
### • They execute control logic and respond to sensor inputs within milliseconds  
### • PLCs directly connect to sensors and actuators to control physical processes  

### What is Modbus?  
### What is Modbus? Modbus is a communication protocol used by industrial devices to exchange information and control operations.  
### How does it work? It follows a simple request-response model where a client requests data and the PLC responds with the requested value accordingly.  
### • Modbus was created in 1979 by Modicon (now Schneider Electric)  
### • It is one of the most widely used industrial communication protocols  
### • Its popularity comes from being simple, reliable, and compatible with many devices 
<img width="1581" height="546" alt="image" src="https://github.com/user-attachments/assets/b23662b5-302c-4f1c-9194-6bf162daee7f" />

### We are going to identify important Modbus registers and coils, as they control the drone delivery system and reveal signs of compromise.  

### The maintenance note documents these addresses and their functions, helping us understand the system configuration accordingly.  

### • `HR0` → Package type selection (`0=Gifts`, `1=Eggs`, `2=Baskets`)  
### • `HR1` → Delivery zone (`1-9` normal zones, `10` emergency disposal)  
### • `HR4` → System signature or attacker's identifier  
### • `C10-C15` → Control inventory verification, protection mechanisms, audit logging, restoration status, and self-destruct functions  
### • Accordingly, these Modbus addresses are critical for investigating and restoring the compromised system  

<img width="1589" height="476" alt="image" src="https://github.com/user-attachments/assets/00ea981c-870e-4f1b-827a-e208fb4daf1d" />

### The Security Problem  
### • No Authentication → Any client can connect and send commands  
### • No Encryption → All communication is transmitted in plaintext  
### • No Authorization → Connected users can read or modify any value  
### • No Integrity Checking → Commands can be altered without cryptographic verification  
<img width="1587" height="325" alt="image" src="https://github.com/user-attachments/assets/405ddf8f-46a8-4671-80ce-b0b42eeee25f" />

## Task 4 Practical
### Now the fun part begins! Turn on the Attackbox
<img width="907" height="799" alt="image" src="https://github.com/user-attachments/assets/6f7a1aec-6eda-4ef6-87c7-4cbd08d3f985" />

### Step 1 - Recon: what’s actually exposed?
<img width="899" height="771" alt="image" src="https://github.com/user-attachments/assets/c785d1d7-c075-4947-9817-c72220045279" />

### We can see two scripts open reconnaissance script 
<img width="903" height="678" alt="image" src="https://github.com/user-attachments/assets/e3f2ecf9-e979-4c18-9c01-177f63581fad" />

<img width="899" height="440" alt="image" src="https://github.com/user-attachments/assets/84edf759-0468-452f-a79e-ada4cf9a6101" />

### We can see the coils and holding registers which attacker can change. Lets turn the script to see the values
<img width="886" height="693" alt="image" src="https://github.com/user-attachments/assets/696aef41-b106-453a-9ded-ab20fd3ea81c" />

### We can see the values that are set by the attack by directly access modbus through tcp on port 502
### Open restore_christmas.py script to restore the values
<img width="897" height="698" alt="image" src="https://github.com/user-attachments/assets/4fa54465-6827-4dc5-b044-cb54a8d30472" />

### Enter ./restore_christmas.py to run the script 
<img width="891" height="418" alt="image" src="https://github.com/user-attachments/assets/64347df0-b45f-4a8c-b7b2-4ce861143562" />

<img width="892" height="633" alt="image" src="https://github.com/user-attachments/assets/5f82c9b4-fa05-4fcb-b43d-47a3c33c758f" />

### Success christmas is saved and we have received the flag : THM{eGgMas0V3r}
<img width="1576" height="343" alt="image" src="https://github.com/user-attachments/assets/4a6af29d-29a3-4fe3-b7b6-fae27a4b5452" />

## Congratulations !!! We have Successfully Completed the room.
<img width="1623" height="440" alt="image" src="https://github.com/user-attachments/assets/c2f67118-793c-4d94-b87f-65ae5187daa9" />









