# Amazon-Web-Services
This is the final project of the Udacity Nanodegree "Full Stack Web Developer". The aim of this project is to secure and setup a Linux server and to host the Item-Catalog project. The Linux Server Instance was setup using Amazon Lightsail. 

## Steps
In the following sections, the steps required to setup the project are described.

### Create a Linux Server Instance on Amazon Lightsail and establish an SSH connection
1. Create an Amazon Web Services Account
2. Create an Ubuntu Linux Server Instance on Amazon Lightsail
3. Create a static IP address *StaticIP-Vrginia-1-Lilly-Udacity* and attach it to the instance
4. Add Port 2200 to the external firewall via the "Networking" tab
5. Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
6. Download the SSH default key pair from Lightsail
7. Connect to the Instance via PuTTY using the User Ubuntu and using the private key for authentication
---
### Update all currently installed packages and autoremove any irrelevant packages
1. `sudo apt-get update`
2. `sudo apt-get upgrade`
3. Selected "*keep the local version currently installed*" when asked "A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified."
4. `sudo apt-get autoremove`
---
### Change the SSH port from 22 to 2200
1. Open `sudo vi /etc/ssh/sshd_config` and change Port from **22** to **2200**
2. `sudo /etc/init.d/ssh restart`
3. Close connection
---
### Configure the Uncomplicated Firewall (UFW) to allow only SSH, HTTP, and NTP connections and enable the Firewall
**In order to establish the best result first deny any incoming connection, then open only the desired ports**
1. Start a new connection via PuTTY to Port 2200
2. `sudo ufw default deny incoming`
3. `sudo ufw default allow outgoing`
4. `sudo ufw allow 2200/tcp`
5. `sudo ufw allow www`
6. `sudo ufw allow ntp`
7. `sudo ufw enable`
---
### Create a new user named grader who receives sudo rights 
1. `sudo adduser grader`
2. Add a Full Name: "Udacity Grader"
3. `sudo ls /etc/sudoers.d`
4. `sudo cp /etc/sudoers.d/90-cloud-init-users /etc/sudoers.d/grader`
5. `sudo vi /etc/sudoers.d/grader`
6. Change **ubuntu** to **grader**: `sudo su - grader`
7. `mkdir .ssh`
8. `chmod 700 .ssh`
9. `touch .ssh/authorized_keys`
10. `chmod 600 .ssh/authorized_keys`
11. `ssh-keygen`
12. Retrieve the public key `ssk-keygen -y` and copy and paste it into `.ssh/authorized_keys`
13. Save the private key on computer and save as `grader-key.pem`
14. Use PuTTYgen to generate the private key
---
### Install Apache2, PostgreSQL, and Git

**Required packages are: apache2, libapache2-mod-wsgi, postgresql, git**

Note: WSGI might have to be enabled (see steps below)

1. `sudo apt-get install apache2`
2. `sudo apt-get install libapache2-mod-wsgi`
3. `sudo a2enmod wsgi`
4. `sudo service apache2 restart`
5. `sudo apt-get install postgresql`
6. `sudo apt-get install git`
---
### Create a new PostgreSQL user calles catalog and create the database for the project
1. `sudo -u postgres psql`
2. Create a new user with password: `CREATE USER catalog WITH PASSWORD catalog;`
3. Give the user the permission to create a database: `ALTER USER catalog CREATEDB;`
4. Create the items_db database which is owned by the user catalog: `CREATE DATABASE items_db WITH OWNER catalog;`
5. Revoke all public rights from the database: `REVOKE ALL ON SCHEMA public FROM public;`
6. Allow only the user catalog to create tables: `GRANT ALL ON SCHEMA public TO catalog;`
Exit with `CTRL + d`
---
41. `sudo mkdir /home/udacity`
42. `cd /home/udacity`
43. `sudo git init`
44. `sudo git clone https://github.com/LetitiaK/Item-Catalog`
---
45. `sudo apt-get install python-pip`
46. `sudo pip install sqlalchemy`
47. `sudo pip install flask`
48. `sudo pip install oauth2client`
49. `sudo pip install psycopg2`
`sudo pip install requests`
---
50. `sudo -u postgres psql`
51. `CREATE DATABASE items_db;`
Exit with `CTRL + d`
---

### 
