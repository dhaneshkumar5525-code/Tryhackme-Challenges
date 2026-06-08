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

### Now for the password navigate to the network tab and we can observe the magic question: What is the password for this level?
<img width="1176" height="709" alt="image" src="https://github.com/user-attachments/assets/7eaea99d-b312-417f-8d59-4f405e224a7f" />

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

<img width="1225" height="187" alt="image" src="https://github.com/user-attachments/assets/6dba94eb-ee37-4074-955e-af3c1b11cf0f" />

### We have unlocked the outer gate
<img width="915" height="755" alt="image" src="https://github.com/user-attachments/assets/57ccbccf-4695-43e8-8405-a6139883af02" />

## Task 4 Second Lock - Outer Wall
### We are going to identify the guard's name and save the encoded output, as it will be needed later in the challenge.  
### We will then extract and encode the magic question to obtain the encoded password from the guard accordingly.  

### • Find the guard's name  
### • Save the encoded output for later use  
### • Extract the magic question from the challenge and encode the magic question  
### • Accordingly, retrieve the encoded password from the guard  

### Click on the outer gate and we can see the guard name : CarrotHelm
<img width="1167" height="607" alt="image" src="https://github.com/user-attachments/assets/eda0d57b-f5c6-4d25-a0cf-7366b4c6dec4" />

### Lets encode the guardname in base64 
<img width="1176" height="633" alt="image" src="https://github.com/user-attachments/assets/8e28eca6-c88b-45fa-820c-4059e1da57b6" />

### Navigate to the network tab to see the magic question
<img width="1178" height="375" alt="image" src="https://github.com/user-attachments/assets/42bfeeb0-17b2-4da6-b185-8bc4e8f3f1c1" />

### Encode "Did you change the password? in cyberchef 
<img width="1179" height="540" alt="image" src="https://github.com/user-attachments/assets/cfeb4d93-4200-482c-8709-b6e6d1d819aa" />

### RGlkIHlvdSBjaGFuZ2UgdGhlIHBhc3N3b3JkPw== Send it in the bunnygram
### Here is the response from the guard
<img width="1178" height="631" alt="image" src="https://github.com/user-attachments/assets/b9df95d8-d734-4567-9424-1b527749bacb" />

### SGVyZSBpcyB0aGUgcGFzc3dvcmQ6IFUxaFNkbUpIVWpWaU0xWXdZakpPYjFsWE5XNWFWMnd3U1ZFOVBRPT0=
### Copy it to the cyberchef and here is the encoded password
<img width="1180" height="500" alt="image" src="https://github.com/user-attachments/assets/a6e0aef8-e2fd-4af3-b7a6-5f273200c6ad" />

### Base64 Decode: Here is the password: U1hSdmJHUjViM1YwYjJOb1lXNW5aV2wwSVE9PQ==

### Let's Decode the b64 string again:

### String: U1hSdmJHUjViM1YwYjJOb1lXNW5aV2wwSVE9PQ==

<img width="1177" height="635" alt="image" src="https://github.com/user-attachments/assets/c6911e23-f0aa-4ccc-9987-c83ad622b144" />

### B64 Encode: SXRvbGR5b3V0b2NoYW5nZWl0IQ==
### Let’s Decode the b64 string again: SXRvbGR5b3V0b2NoYW5nZWl0IQ==
<img width="1180" height="628" alt="image" src="https://github.com/user-attachments/assets/23da2965-8b1c-4ff7-9156-d924c004a704" />

### B64 Encode: Itoldyoutochangeit!
### Now enter both encoded username and the password to login 
<img width="1179" height="650" alt="image" src="https://github.com/user-attachments/assets/b435f8cc-f0b8-4fc6-b4d1-4a316b48ef14" />

### Outer wall lock has been breached

### Task 5 Third Lock - Guard House
### Lets unlock this guard house 
### First part : Encode the guard name LongEars
<img width="1176" height="704" alt="image" src="https://github.com/user-attachments/assets/09900973-4f56-440b-9099-e2760a4856a2" />

### We got the username TG9uZ0VhcnM=
### Navigate to the Network tab and level 3 
<img width="1177" height="285" alt="image" src="https://github.com/user-attachments/assets/581c96a1-ac0c-435c-853e-0533e94666e5" />

### There is no magic question !! instead of the magic question there is something called receipe key. Lets see what it is used for?
### Navigate to the debugger and app.js
<img width="1177" height="347" alt="image" src="https://github.com/user-attachments/assets/d6777d5e-4a52-4fb1-857e-5f64cba6fdf7" />

### It seems like we have to decode a Base64 string to XOR using the given recipe key given at header: cyberchef
### The challenge says if you want the password just ask the guard. So we are going to send Password Please. in base64
<img width="1178" height="635" alt="image" src="https://github.com/user-attachments/assets/5fde3978-5e99-4b5f-97bc-029ac5a1b28b" />

### Base 64 Encode: UGFzc3dvcmQgUGxlYXNlPw== Send it in the bunnygram
### We have received response from the LongEars 
<img width="1176" height="516" alt="image" src="https://github.com/user-attachments/assets/771aaf4c-6b29-4064-b8e8-d09fed57ef62" />

### SGVyZSBpcyB0aGUgcGFzc3dvcmQ6IElRd0ZGakFXQmdzZg==
### Decode the response in base64
<img width="1179" height="535" alt="image" src="https://github.com/user-attachments/assets/4eb608e6-ae75-428c-ac02-2df8f74ec413" />

### Here is the password: IQwFFjAWBgsf
### Now Take this encoded password and select Xor in the key section enter Cyberchef to see the final password
<img width="1177" height="632" alt="image" src="https://github.com/user-attachments/assets/d2b76832-fa67-4a48-abba-c4dcaab5f804" />

### We have received the password : BugsBunny
### Now enter both the username and the password to unlock the gate
<img width="1153" height="210" alt="image" src="https://github.com/user-attachments/assets/1515f719-df07-4fa8-abf1-1fbb56474dca" />

### Guard lock has been breached 
<img width="1216" height="206" alt="image" src="https://github.com/user-attachments/assets/8da07ebc-82fe-4514-bdcf-97afee863044" />

## Task 6 Fourth Lock - Inner Castle
### We are going to analyze the login logic, as this helps us understand how the authentication process works in this level.  
### We will focus only on the login mechanism, as header information is not required for this challenge accordingly.
### Encoding the guard name Lenny 
<img width="1177" height="543" alt="image" src="https://github.com/user-attachments/assets/eb77ee9b-3221-4d26-958f-b9b8f7657d20" />

### TGVubnk=
### Lets send password please. to lenny guard 
<img width="1176" height="634" alt="image" src="https://github.com/user-attachments/assets/809481ff-f3a0-4c04-9e42-9ac5949bb892" />

### UGFzc3dvcmQgUGxlYXNlPw==
### Lenny guard response
<img width="1179" height="334" alt="image" src="https://github.com/user-attachments/assets/c3534ed2-964c-4bb0-b89d-511b62be679f" />

### Guard Response: SGVyZSBpcyB0aGUgcGFzc3dvcmQ6IGI0YzBiZTdkN2U5N2FiNzRjMTMwOTFiNzY4MjVjZjM5
### Decode it again 
<img width="1178" height="541" alt="image" src="https://github.com/user-attachments/assets/e3463a4a-5390-4ccf-a6d6-ec047fee4d09" />

### We have received a Md5 hash b4c0be7d7e97ab74c13091b76825cf39
### I have used hashes.com to decode the hash 
<img width="1161" height="462" alt="image" src="https://github.com/user-attachments/assets/69443ce3-92da-4e9c-9d65-7f5517239905" />

### Hash in plain text: passw0rd1
### Lets enter both username and password to unlock the gate
<img width="1179" height="390" alt="image" src="https://github.com/user-attachments/assets/95cfaf9a-8d80-48a3-8dbf-43cd0f3f3c8a" />

### Inner castle lock has been breached 
<img width="1250" height="190" alt="image" src="https://github.com/user-attachments/assets/63149e19-a75c-4876-a5bc-f979975f0ba0" />

## Task 7 Fifth Lock - Prison Tower
### Final Challenge  

### We are going to break the last lock, as McSkidy has warned that different decoding mechanisms may be used for the final password. ### We will identify the correct decoding approach and apply it accordingly to complete the challenge.  
### • This is the final hurdle of the challenge  
### • McSkidy provides a hidden warning message  
### • The last lock uses different mechanisms than the previous ones  

### Lets encode the guards name carl 
<img width="1179" height="532" alt="image" src="https://github.com/user-attachments/assets/d430c709-3e2d-46d2-b081-c5e911d0e791" />

### For the password navigate to the debugger tab and app.js and look for the level 5 condition
<img width="1178" height="345" alt="image" src="https://github.com/user-attachments/assets/f21ec9bf-ad46-40f2-8f52-fb3f6b018890" />

### It can be either receipe R1,R2,R3 or R4 (Possible decreption)
### To find the receipe id navigate to the network tab and level 5 
<img width="1178" height="345" alt="image" src="https://github.com/user-attachments/assets/b6abe9e5-6072-480e-a8b7-d455d77c3802" />

### We can see the receipe id R2
<img width="506" height="306" alt="image" src="https://github.com/user-attachments/assets/21ae8863-bfbd-43ac-a973-adaa879fef67" />

### From Base64 => From Hex => Reverse 
### Now we will use password please.
<img width="1178" height="540" alt="image" src="https://github.com/user-attachments/assets/56733237-c8dd-4295-86d6-b1b84c274e20" />

### Paste it in the bunnygram and  here is the response from the guard carl 
<img width="1180" height="539" alt="image" src="https://github.com/user-attachments/assets/22852f1d-4511-4567-b29b-9ea3f651ccb1" />

### SGVyZSBpcyB0aGUgcGFzc3dvcmQ6IE56SXpNelppTmpNek1EWmpOREkyT0RZek16UXpNemN5TkRJM01qTXhNelU9
<img width="1178" height="467" alt="image" src="https://github.com/user-attachments/assets/3fa44bd1-6e8d-45c4-822f-9353aee7b3e3" />

###  Here is the password: NzIzMzZiNjMzMDZjNDI2ODYzMzQzMzcyNDI3MjMxMzU=
### Now the important part we will use a sequence of decryptions base64 then from hex then reverse string 
<img width="1180" height="559" alt="image" src="https://github.com/user-attachments/assets/1c81dd48-ae1a-4f6e-abed-4b6ff726f3a9" />

### We have received 51rBr34chBl0ck3r. Now enter both username and passwords 
<img width="1176" height="527" alt="image" src="https://github.com/user-attachments/assets/46da52d8-64c3-4485-a6ca-7916e87470cc" />

### We have cleared the path for mcskidy to escape!
### We have received the final flag  : THM{M3D13V4L_D3C0D3R_4D3P7}
<img width="1176" height="526" alt="image" src="https://github.com/user-attachments/assets/d2d381fd-0889-4ef8-bcc2-fb945ed728fe" />

### Congratulations !!! We have Successfully completed the room.
<img width="1252" height="483" alt="image" src="https://github.com/user-attachments/assets/bca7d124-deb2-41c9-a40c-97524579cef7" />




