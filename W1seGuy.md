# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### W1seGuy
<img width="1659" height="404" alt="image" src="https://github.com/user-attachments/assets/3ae3aa0b-1a8b-4274-ab18-71dbdc546f64" />

### A w1se guy 0nce said, the answer is usually as plain as day.
### Turn on the target machine
<img width="1321" height="167" alt="image" src="https://github.com/user-attachments/assets/e8d1f6c9-ee84-4c55-bb71-03ffb65c339d" />

## Task 1 Source Code
### Another cryptography challenge awaits. Before starting the next task, review the provided source code to understand how the application works.  
### • Download the task files using the **Download Task Files** button  
### • Open and inspect the source code carefully  
<img width="2002" height="2198" alt="use less code" src="https://github.com/user-attachments/assets/3d91d8f9-17a3-4bec-9348-c16c6b0e61ce" />

## Task 2 Get those flags!
### ### Server Information  
### • The challenge server is listening on TCP port **1337**  
### • Connect using **Netcat (nc)** or another TCP client  
### • Interact with the service to analyze its behavior  
### • Gather information that may help solve the cryptography challenge  
### Lets connect to the target machine, enter the command 
### nc 10.10.250.49 1337
<img width="825" height="99" alt="image" src="https://github.com/user-attachments/assets/2dfad531-b082-48b2-8955-7139ff946441" />

### We have received the flag but it was encoded text with the encryption key.
### To know the key we need to know the format. We know the key starts with the THM{ which we are using in the cyberchef|
### Convert To Hex THM{ using the cyberchef
<img width="1920" height="659" alt="image" src="https://github.com/user-attachments/assets/cadb828e-23a0-4d94-b5b6-ba285dd4531e" />

### We can see the first four key produces 8 encoded string so we will use first 8 characters from the encoded flag : 1927la28 as key
<img width="1920" height="696" alt="image" src="https://github.com/user-attachments/assets/aeda3abc-d25b-4bbb-8283-f23fb392fc2b" />

### We can see the encode message MoWS. Now we will use this as key and paste the entire encoded flag in cyberchef and set the value at UTF8
<img width="1920" height="702" alt="image" src="https://github.com/user-attachments/assets/f01b5e77-b319-46e9-aeae-166d1c83a94a" />

### From the given challenge code we know the key is 5 characters but we have only 4. Lets use trail and error method starting from 0-9 and a-z
### Lets start with 1
<img width="1920" height="700" alt="image" src="https://github.com/user-attachments/assets/30784079-49f5-462b-96f3-24045d53602a" />

### This is not the key. I will try every combination and skip to the right key
### After checking every combo  key ends with  p
<img width="1920" height="779" alt="image" src="https://github.com/user-attachments/assets/4ba604a5-f57d-4300-a967-a810e0c0278c" />

### Lets check the key in the challenge : THM{p1alntExtAtt4ckcAnr3alLyhUrty0urxOr}
<img width="1604" height="188" alt="image" src="https://github.com/user-attachments/assets/7fbddc81-3cc6-4bab-bc0c-f4f7296c6e81" />

### Lets paste the encryption key in the terminal
<img width="829" height="122" alt="image" src="https://github.com/user-attachments/assets/69224b63-4518-49c4-afdc-1bbd03af116b" />

### We have found the second key: THM{BrUt3_ForC1nG_XOR_cAn_B3_FuN_nO?}

### Answers 
<img width="1614" height="344" alt="image" src="https://github.com/user-attachments/assets/ac6765ff-b140-48b7-8a38-1a16a735c96a" />

## Congratulations !!! We have Succcessfully Completed the Room.
<img width="1705" height="405" alt="image" src="https://github.com/user-attachments/assets/44aa81f6-95dd-455f-aead-bc39b3882c57" />












