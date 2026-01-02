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




## 3. Threat Model
