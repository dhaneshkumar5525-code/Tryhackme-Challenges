# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### CyberChef - Hoperation Save McSkidy.
### The story continues, and the elves mount a rescue and will try to breach the Quantum Fortress's defenses and free McSkidy.
<img width="1245" height="448" alt="image" src="https://github.com/user-attachments/assets/7b2dba3b-0650-45a7-9fd2-01f2e1c0ea1f" />

## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/875b9f6c-33ee-4293-9a05-c41b677cc4c2" />

### We are going to help McSkidy escape from King Malhare’s Quantum Warren, as five security locks must be disabled to create a safe escape route.  
### We will examine the lock logic and use the built-in guard chat system to gather passwords and important details accordingly.  

### • McSkidy is imprisoned inside the Quantum Warren  
### • Sir BreachBlocker III secured the fortress with strong access controls  
### • Hidden clues were sent through harmless bunny pictures  
### • Five locks must be broken to open the escape route  
### • Accordingly, we must understand the guards’ language to obtain useful information  

### Learning Objectives  
### • Introduction to encoding and decoding  
### • Learn how to use CyberChef  
### • Identify useful information in web applications through HTTP headers  

## Task 2 Important Concepts
### Key Difference Between Encoding and Encryption
### • Encoding changes data into another format for easy storage or transfer, and it can be reversed without a secret key.
### • Encryption changes data into a secure format to protect confidentiality, and it requires a key to decrypt it.
<img width="593" height="498" alt="image" src="https://github.com/user-attachments/assets/21910bc8-4338-4c07-b1ff-e33737cd07cd" />

### CyberChef Overview
### CyberChef(opens in new tab) is also known as the Cyber Swiss Army Knife. Ready to cook some recipes?
<img width="581" height="386" alt="image" src="https://github.com/user-attachments/assets/e12b7621-7d18-4f00-b9c1-4a15eb41bb1e" />

### Simple Example  

### We are going to try our first CyberChef recipe by encoding text into Base64, as this helps us understand basic encoding and decoding.  
### We will use the `To Base64` and `From Base64` operations with the input `IamRoot` to demonstrate chained operations accordingly.  

### • Open CyberChef using the online version or the offline version in AttackBox  
### • Drag and drop the `To Base64` operation into the Recipe area  
### • Enter `IamRoot` in the Input section to encode it  
### • Add `From Base64` to decode it back to the original text  
### • Accordingly, this shows how multiple operations can be chained together 
<img width="1920" height="759" alt="image" src="https://github.com/user-attachments/assets/60c3751c-b5a0-4e36-90f1-5097b027d8f8" />

### Congratulations! You took the first steps to become a master Chef.

### Inspecting Web Pages  

### We are going to inspect web pages beyond the visible content, as browsers also receive additional hidden information that can be useful for investigation.  
### We will access browser inspection tools to view this extra data and use it during the challenge accordingly.  
### • Web pages contain more than just the rendered content  
### • Browsers receive hidden details along with the visible page  
<img width="592" height="570" alt="image" src="https://github.com/user-attachments/assets/e32c111d-b551-4a36-b115-d4f01cd7ac30" />

## Task 3 First Lock - Outer Gate
### start the target machine, give it a few minutes to boot up, and then, from the AttackBox, you can access the web app at http://10.67.146.57:8080
<img width="1177" height="797" alt="image" src="https://github.com/user-attachments/assets/ca081bee-52d9-406b-a898-6186e50ad24d" />

### Lets help Mcskidy to escape my unlocking the gates
### What is the password for the first lock?

### Naviagte to the outer gate
<img width="1167" height="638" alt="image" src="https://github.com/user-attachments/assets/45872f3d-018e-4d90-8eb9-b157a9f7bbe3" />

<img width="1175" height="697" alt="image" src="https://github.com/user-attachments/assets/9c6e16ba-9a79-4243-bec5-f58591fdeba6" />

### We can see the bunnygram encoding
### Right click inspect
<img width="522" height="626" alt="image" src="https://github.com/user-attachments/assets/5f3c462b-ab80-4946-8a2a-2bbc2802ebb8" />

### Select network tab and refresh the page
<img width="1176" height="646" alt="image" src="https://github.com/user-attachments/assets/1cfe7aba-7c9a-4d0e-a499-d31ea29aa1a5" />

### Responses
<img width="1179" height="280" alt="image" src="https://github.com/user-attachments/assets/12c2681c-5e4f-491d-bb22-ee814d24c2d2" />

### Lets decode the encoding using cyberchef
<img width="1179" height="627" alt="image" src="https://github.com/user-attachments/assets/df1f3cb9-65ab-4b5d-a597-253c5ae1890c" />

### The decoded message is All hail King Malhare!
### Lets figure out the username and the password, Right click inspect > Debugger > ststic > Js app to see the the logic
<img width="1176" height="759" alt="image" src="https://github.com/user-attachments/assets/d79a00e9-ea1f-4084-a184-267444f13953" />

### Search for the User login logic
### We can see userok= atob(usr) === guardName;
### a to b is a string in java script that converts guardname into base64 
### For password, we can see the logic Level 1 = From base64 and Level 2 = Double from base64
<img width="1177" height="378" alt="image" src="https://github.com/user-attachments/assets/89f0961f-da6a-4d2a-bbfd-e6938b1d7d1a" />

### Lets convert the guardname into base64 using cyberchef
<img width="1180" height="495" alt="image" src="https://github.com/user-attachments/assets/bed603e3-b40c-42ff-af9c-cf7add2f005d" />

### Now for the password navigate to the network tab and we can observe the magic question: What is the password for this level?<img width="1176" height="709" alt="image" src="https://github.com/user-attachments/assets/7eaea99d-b312-417f-8d59-4f405e224a7f" />

### Convert in the base64
<img width="1176" height="492" alt="image" src="https://github.com/user-attachments/assets/1b175d01-6e17-4ab2-bf98-8857338e4124" />

### This encoded message is sent to the bunnygram and received a different encoded message
<img width="1176" height="462" alt="image" src="https://github.com/user-attachments/assets/9eb6d4b6-c06f-41ab-bd17-3231373e70eb" />

### lets decode the encoded message received 
<img width="1177" height="633" alt="image" src="https://github.com/user-attachments/assets/fa805014-a2b5-41e4-9984-463cecef0d98" />

### Decode again
<img width="1180" height="492" alt="image" src="https://github.com/user-attachments/assets/8edf0b99-189a-4cf8-9997-f108c4928be8" />

### We have received the password. Now enter the username and the password
<img width="1151" height="254" alt="image" src="https://github.com/user-attachments/assets/22b3e0f0-26ed-4e91-a328-80e3bc0ff973" />

### We have unlocked the outer gate
<img width="915" height="755" alt="image" src="https://github.com/user-attachments/assets/57ccbccf-4695-43e8-8405-a6139883af02" />










