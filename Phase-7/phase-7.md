# Phase 7 – Security Audit and System Evaluation 
## Objectives
Conduct a security audit and evaluate overall system configuration
---

## 1. Security Audit Report


### a. Running the Baseline Security Audit (Lynis)

Firstly in order to understand what changes I could make to the security of my system I ran a Lynis Security audit, I did this before so I could see its suggestions and warnings and also get a hardening score, so I can compare my system after the changes and see if it has increased, showing an increase in the system's overall efficiency 

#### Baseline Hardening Score ####
![BLynis.png](Images/BLynis.png)

#### Warnings and Suggestions ####

![BWSLynis.png](Images/BWSLynis.png)

This screenshot only shows a small percentage of the suggestions as there was a multitude of them.

### b. Rectifying the Warning ###
When I ran the Security Audit the only warning that came up was one that warned me that some of my packages had some vulnerabilities which translates that not all packages were fully patched, leading me open to surface level attacks 

![BWSLynis.png](Images/BWyis.png)
#### Solution: ####
I decided to just enable unattended security updates, this means that my system will automatically update itself to protect against vulnerabilites 

![BWSLynis.png](Images/BWSys.png)

### c. Working on Suggestion 1 ###

![BWSLynis.png](Images/BWyis.png)

The first suggestion I decided to take up was the suggestion to change Fail2Ban configuration protection,this is because Fail2Ban uses jail.conf which is a default file, meaning that it is open for package updates to overwrite it 

#### Solution: ####
In order to tackle package updates overwriting my file, I created a local override file which overrides defaults meaning my Fail2Ban stays consistent and isn't overriden.

![BWSLynis.png](Images/BSyis.png)

### d. Working on Suggestion 2 ###
The second suggestion I picked up was the one that recommended installing needrestart. This is because it scans all the running services after updates and highlights which ones are still using old libraries, thus needing a restart. This will help my server to be generally more secure and more efficient, especially since it will be taking advantage of the newest patch updates.

### Solution ### 
As the suggestion wrote, I just installed needrestart on my server 

![BWSLynis.png](Images/Syis.png)


