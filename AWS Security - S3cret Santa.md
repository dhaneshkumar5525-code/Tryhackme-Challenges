# Hi, I'm a Cybersecurity Analyst 
### Focused on analyzing threats, demonstrating attack scenarios, and conducting security investigations.
<img width="1690" height="423" alt="image" src="https://github.com/user-attachments/assets/39b0b7d6-0442-451a-a3bb-a3e474f57f83" />

### AWS Security - S3cret Santa
### Today, We are going to learn the basics of AWS enumeration.
## Task 1 Introduction
<img width="1200" height="407" alt="image" src="https://github.com/user-attachments/assets/b0362f66-b856-47f4-9027-3452d6efe659" />

### Cloud Credentials Investigation  
### We are going to investigate a set of cloud credentials discovered in Sir Carrotbane’s office, as they may provide access to TBFC’s cloud environment.  
### The goal is to validate and use these credentials safely to regain visibility into the cloud network accordingly.  
### • An infiltrated elf discovered cloud credentials on Sir Carrotbane’s desktop  
### • The credentials may provide access to TBFC’s cloud infrastructure  

### Learning Objectives  

### • Learn the fundamentals of AWS accounts and cloud environments  
### • Understand how to enumerate account privileges from an attacker's perspective  
### • Become familiar with using the AWS CLI for cloud investigations  

### Q1. Run aws sts get-caller-identity. What is the number shown for the "Account" parameter?
### Lets enter the commmand virtual machine
<img width="908" height="428" alt="image" src="https://github.com/user-attachments/assets/1d9a1088-0655-471b-85cb-6c64ff68c8ed" />

### We can see the account number : 123456789012
## Task 2 IAM: Users, Roles, Groups and Policies
### AWS IAM Overview  
### • IAM controls who can access AWS resources and what actions they can perform  
### • Users should only receive the permissions required for their role (least privilege)  
### • Misconfigured permissions can grant excessive access to sensitive resources  

### IAM Users  
<img width="391" height="488" alt="image" src="https://github.com/user-attachments/assets/4892bdf9-c333-4404-b7d8-1366d04c89ca" />

### • An IAM user represents a single AWS identity  
### • Users access AWS using passwords or access keys  
### • Permissions can be assigned directly to users  
### • Permissions control access to AWS resources and actions 

### IAM Groups  
<img width="640" height="640" alt="image" src="https://github.com/user-attachments/assets/646865f2-2bd7-489d-ba46-c313a67394f7" />

### • IAM groups are collections of multiple users  
### • Permissions can be assigned to the group instead of individual users  
### • Users inherit permissions from the groups they belong to  
### • This simplifies access management and permission updates  

### IAM Roles 
<img width="900" height="600" alt="image" src="https://github.com/user-attachments/assets/dc48fb9d-9379-4295-a63a-673d7f422d37" />

### • IAM roles provide temporary permissions in AWS  
### • Roles can be assumed by users, services, or external accounts  
### • Permissions depend on the role being assumed  
### • Roles help grant specific access without using permanent credentials  

### IAM Policies  

### • IAM policies are JSON documents that define permissions  
### • `Action` → What actions are allowed  
### • `Resource` → Which resources can be accessed  
### • `Condition` → When the permissions apply  
### • `Principal` → Who receives the permissions  
### Consider the following hypothetical policy
<img width="1153" height="550" alt="image" src="https://github.com/user-attachments/assets/b9ca5361-c49c-40cd-b31c-992309bbfa04" />

### Q. What IAM component is used to describe the permissions to be assigned to a user or a group?
### Policy
<img width="1239" height="190" alt="image" src="https://github.com/user-attachments/assets/d02f6956-8142-4067-8d67-0e01720671f8" />

## Task 3 Practical: Enumerating a User's Permissions
### Q. What is the name of the policy assigned to sir.carrotbane?
### To know the name of the policy enter command 
### aws iam list-user-policies --user-name sir.carrotbane 
<img width="907" height="270" alt="image" src="https://github.com/user-attachments/assets/76860c9b-808f-4ce1-8151-75e55e67c69e" />

### We can see one policy named : SirCarrotbanePolicy
## Task 4 Assuming Roles
### Q. Apart from GetObject and ListBucket, what other action can be taken by assuming the bucketmaster role?
### Commands are given in the challenge to see the policy
<img width="1261" height="284" alt="image" src="https://github.com/user-attachments/assets/82b75a4e-2ac8-4b4c-920f-8143f6483626" />

### Enter the command 
<img width="906" height="564" alt="image" src="https://github.com/user-attachments/assets/fcdab336-2540-4a0e-86fb-1be2a79cf86e" />

### Here is the policy
<img width="905" height="811" alt="image" src="https://github.com/user-attachments/assets/87aa1111-29fa-4c50-8630-89f34bc0f101" />

### Here we can see 3 actions S3 GetObject and ListBucket and ListAllMyBuckets
### Answer : ListAllMyBuckets

## Task 5 Grabbing a file from S3
### What is S3?
<img width="600" height="900" alt="image" src="https://github.com/user-attachments/assets/f2d57664-5d5b-44ae-9dea-3ce7932e0c56" />

### • Amazon S3 (Simple Storage Service) is AWS's object storage service  
### • It stores files such as images, documents, logs, and backups  
### • Data is stored inside containers called **Buckets**  
### • A bucket is similar to a cloud-based directory for storing files  

### Now, let's see what our newly gained access to Sir Carrotbane's S3 bucket provides us.
<img width="1215" height="387" alt="image" src="https://github.com/user-attachments/assets/ee241ae1-1540-46a6-9f60-20ecf778cc4f" />

### Lets see what is our role information. Enter the command aws iam list-roles  
<img width="907" height="760" alt="image" src="https://github.com/user-attachments/assets/f3943f60-768b-40e7-ad1e-9ba02fabad6d" />

### We can see the Bucketmaster as Rolename and we need this arn (Attach role name) information
### Now we can produce credentials, enter this command 
### aws sts assume-role --role-arn arn:aws:iam::123456789012:role/bucketmaster --role-session-name TBFC
### Enter to see the output 
<img width="907" height="588" alt="image" src="https://github.com/user-attachments/assets/9f2a6125-4131-4f33-8b10-d62abdab213e" />

### Lets overwrite environment variables, enter command and access key id from the above output
### export AWS_ACCESS_KEY_ID="ASIARZPUZDIKC6BJCPNI" and press enter 
### Now we do same for the Secret access key, enter the secret key from above output in the commmand 
### export AWS_SECRET_ACCESS_KEY="itzRxm0QH1hUdmD6l2gglF3+eE39fTo60l2Uglzr"
### Now we do same for session token ,enter command 
### AWS_SESSION_TOKEN=""FQOGZXIVYXdZEBYaDUOMQDzAqYF26gqab4eIVAXrPzT5jmz7V5jfvkWURib09HtCOhwTmnm-hYPKIA80as5J3jwRM3CdX93z0+uhviefNOLOL7KHi/zHI8ttfh5t29CQ4lG5eUY+gXevm+diMiwI4r181xXLhS1MggRIdJQPi/q+FOCDW687KaQwHJlqrQXgBC54FCEWHr7MUd0js0oVLvgdKCUZeuIHt/cH6p4AWcrFdc5zCbi28LA3ELnhey5C8+cxjKCyxdV8ySBUGZrJjulyZdstPildipltIG9Xm05IHLXIXJV549FCu3v2mfHt7qPlr/l6KDIgOCtDB+fXrb2mKrIFklRnI=",
<img width="908" height="341" alt="image" src="https://github.com/user-attachments/assets/cfaf9520-fb39-45e8-95cc-501b9ec22823" />

### Now we will check the identity, enter the command 
### aws sts get-caller-identity 
<img width="911" height="231" alt="image" src="https://github.com/user-attachments/assets/b2d93df2-4ad1-480e-9eee-8dce6b622c4b" />

### We have successfully assumed the role and the TBFC session
### Now we will see what buckets we have access
### aws s3api list-buckets
<img width="910" height="485" alt="image" src="https://github.com/user-attachments/assets/a7aebf6a-7eae-48f0-b496-8186232b08a2" />

### With out assuming the bucket master role we will get access denied message
### Now we have access to the buckets lets access to the easter secrets bucket
### aws s3api list-objects --buckets easter-secrets-123145
<img width="909" height="650" alt="image" src="https://github.com/user-attachments/assets/03736b10-d278-45dd-8933-ec67df4439d7" />

### We can see cloud_password.txt and lets grab the file
### aws s3api get-object --bucket easter-secrets-123145 --key cloud_password.txt cloud_password.txt
<img width="910" height="244" alt="image" src="https://github.com/user-attachments/assets/4d18ff1b-6907-40dc-85bf-37405b9ab999" />

### Use ls to see the downloaded files in the local host
<img width="908" height="181" alt="image" src="https://github.com/user-attachments/assets/72ed7df5-1eab-4812-ab0d-39dd3eb32339" />

### We can see cloud_password.txt and enter cat to read the file
<img width="909" height="101" alt="image" src="https://github.com/user-attachments/assets/479410fd-7608-45fa-a1cb-85c5544ecad0" />

### We have received the flag : THM{more_like_sir_cloudbane}
<img width="1243" height="220" alt="image" src="https://github.com/user-attachments/assets/4d70b9b5-0607-4638-a197-050edd47ad37" />

## Congratulations !!! We have Succcessfully Completed the Room.
<img width="1655" height="426" alt="image" src="https://github.com/user-attachments/assets/517eed2e-db0c-41c9-bb0b-a6050ee82507" />



