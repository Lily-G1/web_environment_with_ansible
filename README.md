# Web Hosting Environment with Ansible
This repository contains an ansible playbook that automates the configuration of a Linux web hosting infrastructure featuring Apache web server, MySQL & BIND9 DNS   

Various components of the playbook have been seperated into 'roles' for better management, organization and reusability.  
- **base**: Runs the basic tasks involved. These include the installation of packages and dependencies required  
- **mysql**: This role contains tasks that perform a secure MySQL configuration. Ansible used to have a dedicated module for this but it is now deprecated. These tasks 'manually' perform the same actions such as : disable remote root login, create root user + password, remove default test database, etc  
- **dns**: configures Bind9 for our domain. This involves creating a hosted zone, setting up DNS records and specifying forwarders  
- **web-server**: creates a directory that hosts site files, sets permissions, and creates virtual host files  
- **letsencrypt**: runs steps needed to request a SSL certfiicate from letsencrypt. I used this [tutorial](https://www.digitalocean.com/community/tutorials/how-to-acquire-a-let-s-encrypt-certificate-using-ansible-on-ubuntu-18-04) from Digital Ocean to accomplish this  
- **security**: configures firewall settings for the server  
- **play.yml** runs the entire playbook  
- All variables are stored in the '**group_vars**' directory  

## Improvement:
- Enhance security by using ansible-vault to store sensitive information such as passwords  
- Include an Intrusion Detection system to monitor network traffic & protect against malicious activities  
