# Linux-System-Administration
Prepared another Linux server in a simulated environment.

You acted as a system administrator in order to troubleshoot a malfunctioning Linux server.  The senior administrator was quite pleased with your work. Now, they would like you to prepare another server to replace the malfunctioning server. To do so, complete the steps detailed in the Instructions section.

**Step 1: Ensure Permissions on Sensitive Files**

Inspect the file permissions of each of the following files. You should have already done this during an in-class activity, but double check them now. If any file's permissions do not match the descriptions listed here, update the file's permissions.

1. Permissions on /etc/shadow should allow only root read and write access.

    a. Command to inspect permissions:

    answer: ls -l /etc/shadow  
    <img width="247" alt="1ab" src="https://user-images.githubusercontent.com/106919343/200633831-71c5daee-784f-4eb7-9b2c-92c775fe3e5e.png">

    b. Command to set permissions (if needed):

    answer: sudo chmod 600 /etc/shadow  
    

2. Permissions on /etc/gshadow should allow only root read and write access.

    a. Command to inspect permissions:

    answer: ls -l /etc/gshadow  
    <img width="262" alt="2ab" src="https://user-images.githubusercontent.com/106919343/200634447-8d21774e-db86-4ce3-b0de-844de0c58f1f.png">

    b. Command to set permissions (if needed):

    answer: sudo chmod 600 /etc/gshadow


3. Permissions on /etc/group should allow root read and write access, and allow everyone else read access only.

    a. Command to inspect permissions:

    answer: ls -l /etc/group  
    <img width="258" alt="3a" src="https://user-images.githubusercontent.com/106919343/200635134-674c51f5-b3db-410a-bbe6-f40704c21a0d.png">

    b. Command to set permissions (if needed):

    answer: sudo chmod 644 /etc/group


4. Permissions on /etc/passwd should allow root read and write access, and allow everyone else read access only.

    a. Command to inspect permissions:

    answer: ls -l /etc/passwd  
    <img width="251" alt="4" src="https://user-images.githubusercontent.com/106919343/200634826-c667bf68-cdb4-4ad5-a9d7-176e4cf2758e.png">

    b. Command to set permissions (if needed):

    answer: sudo chmod 644 /etc/passwd

**Step 2: Create User Accounts**

1. Add user accounts for sam, joe, amy, sara, and admin with the useradd command.

    a. Command to add each user account (include all five users):
    
    Answer:

      sudo adduser sam  
      sudo adduser joe  
      sudo adduser amy  
      sudo adduser sara  
      sudo adduser admin  
      <img width="356" alt="2-1a" src="https://user-images.githubusercontent.com/106919343/200635535-df864d50-c2fc-4c99-8584-10fd27dfdae3.png">

2. Ensure that only the admin has general sudo access.

    a. Command to add admin to the sudo group:
    
     Answer:

      To check if admin has sudo access:  
      groups admin   
      sudo -lU admin  
      <img width="559" alt="2-a" src="https://user-images.githubusercontent.com/106919343/200635925-04a2d301-7401-460c-a7be-bda19c8ceffb.png">  
      To add admin to sudo group:    
      sudo usermod -aG sudo admin  
      <img width="589" alt="2-a1" src="https://user-images.githubusercontent.com/106919343/200635969-2be04c86-2147-452e-92a8-94a2984bc6e9.png">  
**Step 3: Create User Group and Collaborative Folder**  
Now, you'll run the commands to fully set up a group on your system.  
This requires you to create a group, add users to it, create a shared group folder, and set the group folder owners for this shared folder.  

1. Add an engineers group to the system.  
    a. Command to add group:  
    Answer:  
    sudo addgroup engineers  
    To check group was added:  
    tail /etc/group  
    <img width="344" alt="31-a" src="https://user-images.githubusercontent.com/106919343/200636094-1e56682e-c94d-4ce4-93ae-956fa2c3c176.png">  

2. Add users sam, joe, amy, and sara to the managed group.  
    b. Command to add users to engineers group (include all four users):  
    Answer:  
    Sudo usermod -aG engineers sam  
    Sudo usermod -aG engineers joe  
    Sudo usermod -aG engineers amy  
    Sudo usermod -aG engineers sara  
    <img width="362" alt="32-a" src="https://user-images.githubusercontent.com/106919343/200636151-ead19bea-62fc-4d5f-bd57-44571079a340.png">  

3. Create a shared folder for this group at /home/engineers.  

    a. Command to create the shared folder:  
    Answer:  
    sudo mkdir /home/engineers  

4. Change ownership on the new engineers’ shared folder to the engineers group.  

    a. Command to change ownership of engineers’ shared folder to engineers group:  
    Answer:  
    To see original ownership:  
    ls -l   

    To change ownership:  
    Answer:  
    sudo chown :engineers engineers  

**Step 4: Lynis Auditing**  
The final step on your administrator's list involves running an audit against the system in order to harden it. You'll use the system and security auditing tool Lynis to do so.  
1. Command to install Lynis:  

Answer: sudo apt install Lynis  

2. Command to view documentation and instructions:  

Answer: man lynis

3. Command to run an audit:

Answer: sudo lynis audit system


