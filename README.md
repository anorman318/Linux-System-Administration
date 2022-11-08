# Linux-System-Administration
Prepared another Linux server in a simulated environment.

You acted as a system administrator in order to troubleshoot a malfunctioning Linux server.  The senior administrator was quite pleased with your work. Now, they would like you to prepare another server to replace the malfunctioning server. To do so, complete the steps detailed in the Instructions section.

**Step 1: Ensure Permissions on Sensitive Files**

Inspect the file permissions of each of the following files. You should have already done this during an in-class activity, but double check them now. If any file's permissions do not match the descriptions listed here, update the file's permissions.

1. Permissions on /etc/shadow should allow only root read and write access.

    a. Command to inspect permissions:

    answer: ls -l /etc/shadow

    b. Command to set permissions (if needed):

    answer: sudo chmod 600 /etc/shadow


2. Permissions on /etc/gshadow should allow only root read and write access.

    a. Command to inspect permissions:

    answer: ls -l /etc/gshadow


    b. Command to set permissions (if needed):

    answer: sudo chmod 600 /etc/gshadow


3. Permissions on /etc/group should allow root read and write access, and allow everyone else read access only.

    a. Command to inspect permissions:

    answer: ls -l /etc/group

    b. Command to set permissions (if needed):

    answer: sudo chmod 644 /etc/group


4. Permissions on /etc/passwd should allow root read and write access, and allow everyone else read access only.

    a. Command to inspect permissions:

    answer: ls -l /etc/passwd


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


2. Ensure that only the admin has general sudo access.

    a. Command to add admin to the sudo group:
    
     Answer:

      To check if admin has sudo access:  
      groups admin   
      sudo -lU admin  

      To add admin to sudo group:  
      sudo usermod -aG sudo admin  

**Step 3: Create User Group and Collaborative Folder**  
Now, you'll run the commands to fully set up a group on your system.  
This requires you to create a group, add users to it, create a shared group folder, and set the group folder owners for this shared folder.  

1. Add an engineers group to the system.  
    a. Command to add group:  
    Answer:  
    sudo addgroup engineers  
    To check group was added:  
    tail /etc/group

2. Add users sam, joe, amy, and sara to the managed group.  
    b. Command to add users to engineers group (include all four users):  
    Answer:  
    Sudo usermod -aG engineers sam  
    Sudo usermod -aG engineers joe  
    Sudo usermod -aG engineers amy  
    Sudo usermod -aG engineers sara  

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


