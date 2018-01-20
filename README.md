# Amazon-Web-Services
This is the final project of the Udacity Nanodegree "Full Stack Web Developer"

## Steps
1. Create a static IP address *StaticIP-Vrginia-1-Lilly-Udacity* and attach it to the instance
2. Add Port 2200 to the external firewall via the "Networking" tab
3. Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
4. Download the SSH default key pair from Lightsail
5. Connect to the Instance via PuTTY
---
6. `sudo apt-get update`
7. `sudo apt-get upgrade`
8. Selected "*keep the local version currently installed*" when asked "A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified."
9. `sudo apt-get autoremove`
---
10. `sudo vi /etc/ssh/sshd_config` change Port from **22** to **2200**
11. `sudo /etc/init.d/ssh restart`
12. Close connection
---
13. Start a new connection via PuTTY to Port 2200
14. `sudo ufw default deny incoming`
15. `sudo ufw default allow outgoing`
16. `sudo ufw allow 2200/tcp`
17. `sudo ufw allow www`
18. `sudo ufw allow ntp`
19. `sudo ufw enable`
---
20. `sudo adduser grader`
21. Add a Full Name: "Udacity Grader"
22. `sudo ls /etc/sudoers.d`
23. `sudo cp /etc/sudoers.d/90-cloud-init-users /etc/sudoers.d/grader`



