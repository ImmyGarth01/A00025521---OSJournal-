# Phase 2 – Secruity Planning and Testing Methodology 

## Objectives
Design a security baseline and performance testing methodology
---

## 1. Performance Testing plan 

**Remote Monitoring Methodology:**  
As a part of the project dual system requirement, the Ubunutu servers will be monitored remotely throught the workstation (my laptop) via the SSH (Safe shell)
This will be done utilising the Command Line terminal in which certain commands can be used to monitor different aspects of the system such as its storage and processing usuage. 

Examples include:

top / htop → CPU and process monitoring

free -h → RAM usage

df -h → disk usage

ip addr → network interface and IP status

**Testing Approach:**  
Below I will place a testing flow diagram on how I think the testing approach should go and will go into a little more detail under it

![Testing Approach](Images/TestingApproach.png)

Step 1) Firstly you should establish your current baseline metrics, this will include your current CPU, Network, Memory and Disk Usage, the command line tools needed to do this are highlihgted under the remote monitoring methodology heading above 

Step 2) Here you are creating a fake workload that will be simulating the a real work load. Think about running some extra background tasks, copying large files, anything that gets some extra processes going. Remember that this is to test how the server copes with extra stress

Step 3) Using the same command line tools as step 1, keep checking the metrics, making note of how they compare 

Step 4) Then compare to the industry standards to test that the server is operating to same level 

CPU < 80% average usage over time

RAM	> 20% free memory 

Disk	< 85% full

Network - Below the Max of the Interface Network (In this case it is 1000Mb/S)

I found the network max by typing hte command 'ip link' to find the main network interface which is enp0s3 and then I used the commands: sudo apt update, sudo apt install ethtool -y and sudo ethtool enp0s3 (I used AI to help me find these commands) 

Step 5) With the new acquired knoweldge on the server's faults you can update whatever needs to be done and test it again 



## 2.Security Configuration Checklist 

In order to add some order and simplicity I put 3 checklist points for each suggested subheading

**SSH Hardening:**  

SSH hardening refers to the need to add extra protections around using SSH, making remote access safer. 

1. Disable Root Password Entry - By disabling the root password there is an added protection of using a user login so sudo can be accessed by only those who have the permissions

2. Change the Default SSH port - The default port is 22, which means attackers will search for this port for entry, by changing it to a random port you can reduce the likelyhood of these attacks

3. Incorporate SSH keys - SSH keys are two sided, the public key being on the server and the private on the worksation, meaning that the private key as an addiitonal layer of security



**Firewall Configuration:**  

1. Create a Firewall - This will create an extra barrier, blocking out unwanted connections

2. Limit access to unvetted ports - Only allow for the SHH essential port to penetrate the firewall, this will mean that you aren't allowing access through any unmaned ports

3. Allow Firewall Monitoring - By making your firewall log all blocked and allowed accesses you have a log that you can cross-referenace if anything has gone wrong or any attack is targeted to you



**Mandatory Access Control:**  
Mandatory Access Control (MAC) is more centered around the protection against the permissions given to applications and what they are allowed to do on the server 

1. Enable AppArmour Application - This app is default on Ubunutu servers, it reviews security permissions and restricts access to system resources and protected files

2. Make Sure AppArmor profiles are applied - These are essentially the rules of permissions of your specific server

3. Consistenly review AppArmour Rules - By changing these rules often you are updating the best security strategy for your server at any current time. 

**Automatic Updates:**  
This heading is in reference to making sure you have the latest updates and security patching

1. Enable Unsupervised Updates - By allowing your server to update regardless you are guarenteed to have the most up to date protections, saving time too

2. Priortize Security Updates - Although there may be many updates, make sure to prioritse the security ones so that your server is secure

3. Check your Update History Regulary - If you check the updates for the latest security updates, you'll have a better idea of what protectioisn you have, and if one has failed to download you can be aware of it

**User Privilege Management:**  

1. Make sure to use Standard Accounts - If you use a standard login user account then you can make suer that only the neccessary changes are made using sudo

2. Limited logged Sudo Access - As an exentsion of the last point, make sure you gice sudo access to a limited amount of people, logging who has it as an extra precaution

3. Deleted Dormant Accounts - Delete all accounts that aren't used, this is becasue they can act as an entry point for hackers if not monitored properly 

**Network Security:**  

1. Restrict Network Access - This is dictated by the firewall rules but its always good rule of thumb to check, this is so you only have secure connections 

2. Monitor Network Access - You can do this to detect any unusal activity that could potentailly be a threat 

3. Disable unused Network Services - Any services that are not being used are an avenue that could be exploited, make sure you disable the services that aren't being used


## 3. Threat Model

Below I will highlight some threat scenarios and relate them to the points on the security configuration list which will act as a mitigation strategy
