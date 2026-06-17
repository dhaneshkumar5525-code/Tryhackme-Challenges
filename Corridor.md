# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
### Corridor
<img width="1754" height="415" alt="image" src="https://github.com/user-attachments/assets/2aea5489-84d9-4bd8-800b-8217b311cbd3" />

### Can you escape the Corridor?
### Turn on the Taget machine 
### Ip-10.80.158.190
<img width="1900" height="238" alt="image" src="https://github.com/user-attachments/assets/a2d36edb-0c2c-447c-92e3-1dff7d0cbbbe" />


## Task 1 Escape the Corridor
### Lets navigate to the website search for 10.80.158.190
<img width="1373" height="700" alt="image" src="https://github.com/user-attachments/assets/8a79567b-8d9f-46b2-ab3d-611eb60126dd" />

### Each door leads to an empty room with a unique URL containing a random hash value.
### • Every room has its own unique path in the URL  
### • The path consists of a hash-like hexadecimal string  
### • Different doors generate different hash values  
### • These hashes may be useful for identifying or accessing other locations within the application  

<img width="973" height="344" alt="image" src="https://github.com/user-attachments/assets/fc2e4d43-e194-4084-a6f2-1fe3b1752254" />

### Here we can see hash value added to the url for room one
### c4ca4238a0b923820dcc509a6f75849b
### Now we will use online crackstation to identify the hash
<img width="1886" height="731" alt="image" src="https://github.com/user-attachments/assets/a373ccfd-7aae-4ce5-9fd6-983e4ebe5658" />

### It is a Md5 hash
### Instead of manually opening every door, the hashes can be extracted directly from the page source.

### • Add `view-source:` before the corridor page URL  
### • Open the page source to view the HTML code  
### • Locate the hash values used by the doors  
### • Copy all hashes into a `.txt` file for easier organization and analysis 

<img width="1914" height="892" alt="image" src="https://github.com/user-attachments/assets/44cd9d87-205c-4e8d-9364-30d39baf6f11" />

### c4ca4238a0b923820dcc509a6f75849b
### c81e728d9d4c2f636f067f89cc14862c
### eccbc87e4b5ce2fe28308fd9f2a7baf3
### a87ff679a2f3e71d9181a67b7542122c
### e4da3b7fbbce2345d7772b0674a318d5
### 1679091c5a880faf6fb5e6087eb1b2dc
### 8f14e45fceea167a5a36dedd4bea2543
### c9f0f895fb98ab9159f51fd0297e236d
### 45c48cce2e2d7fbdea1afc51c7c6ad26
### d3d9446802a44259755d38e6d163e820
### 6512bd43d9caa6e02c990b0a82652dca
### c20ad4d76fe97759aa27a0c99bff6710
### c51ce410c124a10e0db5e4b97fc2af39

### We can see all the hashes here.Now paste all the hashes in the crackstation
<img width="1732" height="922" alt="image" src="https://github.com/user-attachments/assets/94a75f9d-d36a-450d-8028-2c82f5698f8b" />

### We can see the hash represents 0-13 encoded numbers.
### Lets send 0 md5 hash encoded hash in the url using cyberchef
### Select Md5 operator in cyberchef
<img width="1920" height="749" alt="image" src="https://github.com/user-attachments/assets/0000ffb1-52b7-42eb-b839-97532b6af932" />

### Lets send this hash in the url
### cfcd208495d565ef66e7dff9f98764da
<img width="1026" height="453" alt="image" src="https://github.com/user-attachments/assets/cb90ac35-345b-48f0-b66f-7ee344c27092" />


### We found the flag: flag{2477ef02448ad9156661ac40a6b8862e}
## Congratulations !!! We have Successfully Completed the Room.
<img width="1785" height="519" alt="image" src="https://github.com/user-attachments/assets/063ccb89-3333-4afa-8e86-114d0b7e37c8" />













