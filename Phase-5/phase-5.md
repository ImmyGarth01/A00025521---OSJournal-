# Phase 5 – Advanced Security and Monitoring Infrastructure 
## Objectives
Implementation advanced security control and develop monitoring capabilities 
---

## 1. Implement Access Control using SELinux or AppArmor , with documentation showing how to track and report on access control settings 

In this case, as i'm operating an ubunut server my MAC will be AppArmor. 

### a. Confirming App Armour is Installed 

![ConfirmAA.png](Images/ConfirmAA.png)

This shows how I have the MAC installed on my server, evidencing that it exists to track and report on access control settings


### b. Confirming App Armour is running 

![RunningAA.png](Images/RunningAA.png)

This shows that App Armour is not only installed but actively running

### c. Presenting loaded App Armour profiles 

![LoadedAAProfiles.png](Images/LoadedAAProfiles.png)

This shows which profiles are currently being tracked and reported on in the access control setting 

### d. Demonstrating the Profiles being enforced 

![EnforceAAProfiles.png](Images/EnforceAAProfiles.png)

The enforcement status of AppArmor profiles was reported, confirming that profiles are actively enforced rather than operating in complain mode

## 2. Configure Automatic Security Updates 

### a. Confirming unattended-upgrades are installed

![CheckInstall.png](Images/CheckInstall.png)

Firstly I checked that the automatic update package was installed

### b. Enabling Automatic Updates

![EnableAuto.png](Images/EnableAuto.png)

Here I am enabling the automatic updates 

### c. Configuration file 

![ConfigFile.png](Images/ConfigFile.png)

By opening up the configuration file I am showing how the securiity repositeries are listed and enabled meaning they will be installed with no intervention 

### d. Verifying Periodic Update Settings 

![VerPeriodUpdate.png](Images/VerPeriodUpdate.png)

This screenshot shows that automatic updates actually run on a scedule, the 1 means they enabled 

### e. Verifying Service and Logs 

![Run&LogConfirm.png](Images/Run&LogConfirm.png)

Here you can see you the service running confirmation and the logs confirming its active 


## 3. Configuration of Fail2ban

Fail2Ban is an intrusion prevention tool. It monitors log files and automatically blocks IPs with too many failed login attempts.

### a. Install Fail2Ban 
![InstallFail2Ban.png](Images/InstallFail2Ban.png)

![Install2.png](Images/Install2.png)

Seen in the screenshots above, I have installed Fail2Ban, I screenshotted parts of the installation message as it was rather long 

### b. Check Fail2Ban Status 

![Fail2BanStatusCheck.png](Images/Fail2BanStatusCheck.png)

Here I am jsut checkign the status and as you can see it is running 

### c. Checking Jail Configuration

Jail  = A set of rules that define what to monitor and how to respond 

![JailConfigurations.png](Images/JailConfigurations.png)

In this screenshot you can see what is being monitored and the jail configured. As I just installed Fail2Ban the default 1 jail for SSH is being shown 

### d. Showing Jail Information 

![JailInfo.png](Images/JailInfo.png)

This is a log of what attemeotes and bands have been made, showign that my Fail2Ban is being enforced
