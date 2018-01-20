# Amazon-Web-Services
This is the final project of the Udacity Nanodegree "Full Stack Web Developer"

## Steps
1. Create a static IP address *StaticIP-Vrginia-1-Lilly-Udacity* and attach it to the instance
2. Add Port 2200 to the external firewall via the "Networking" tab
3. Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)


1. `sudo apt-get update`
2. `sudo apt-get upgrade`
3. Selected "*keep the local version currently installed*" when asked "A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified."
4. `sudo apt-get autoremove`
5. `sudo vi /etc/ssh/sshd_config` change Port from **22** to **2200**
6. `sudo /etc/init.d/ssh restart`
7. Add Port 2200 to the external firewall via the "Networking" tab



6. `sudo ufw default deny incoming`
7. `sudo ufw default allow outgoing`
8. `sudo ufw allow 2200/tcp`
9. `sudo ufw allow www`
10. `sudo ufw allow ntp`
11. Create a static IP address: *StaticIP-Vrginia-1-Lilly-Udacity*
12. Download and install PuTTY
