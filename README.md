Secure Linux Cloud Server Deployment

Project Description
This project demonstrates how to launch, secure, harden, and deploy a cloud Linux server manually, following real-world DevOps and security best practices.

I manually set up a public-facing Ubuntu server, hardened it against attacks, deployed a custom Nginx web server, and verified full security operations.



Skills Demonstrated

- Linux server administration (Ubuntu)
- Cloud deployment and static IP management (AWS Lightsail)
- SSH security hardening (key-only access, custom port)
- UFW firewall setup (minimal ports open)
- Intrusion prevention (Fail2Ban)
- Automated security patching (Unattended Upgrades)
- Web server deployment (Nginx)
- Real-world debugging and troubleshooting

---

Technologies Used

- Ubuntu 22.04 LTS
- AWS Lightsail
- OpenSSH
- UFW (Uncomplicated Firewall)
- Fail2Ban
- Nginx Web Server

---

Key Security Steps Completed

- Launched a fresh Lightsail Ubuntu instance
- Attached a Static Public IP
- Created a new user (ruben) with sudo privileges
- Configured SSH key authentication only (no passwords)
- Changed SSH port from 22 to 2222
- Installed and configured UFW firewall
- Allowed only ports 80 (HTTP) and 2222 (SSH)
- Installed Fail2Ban for intrusion prevention
- Enabled automatic security updates with safe reboot configuration
- Deployed a custom landing page with Nginx

---

Key Commands Used

```bash
# SSH into server
ssh -i ~/Desktop/LightsailDefaultKey-eu-north-1.pem -p 2222 ruben@13.61.161.132

# Create user and configure SSH
sudo adduser ruben
sudo usermod -aG sudo ruben
sudo mkdir /home/ruben/.ssh
sudo cp ~/.ssh/authorized_keys /home/ruben/.ssh/
sudo chown -R ruben:ruben /home/ruben/.ssh
sudo chmod 700 /home/ruben/.ssh
sudo chmod 600 /home/ruben/.ssh/authorized_keys

# SSH Hardening
sudo nano /etc/ssh/sshd_config
# (Change Port to 2222, disable root login, disable password authentication)
sudo systemctl restart ssh

# Install and configure UFW
sudo apt install ufw -y
sudo ufw allow 2222/tcp
sudo ufw allow 'Nginx HTTP'
sudo ufw enable
sudo ufw reload

# Install Fail2Ban
sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban

# Configure automatic updates
sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure --priority=low unattended-upgrades

# Install Nginx
sudo apt install nginx -y
sudo systemctl enable nginx

# Set up custom landing page
sudo nano /var/www/html/index.html
```

---



Author

Ruben
[GitHub Profile](https://github.com/rubentotterman)



---

Screenshots


Example:
[Webpage]()

---

# 📈 Project Status

✅ Secure Linux server deployed and hardened.  
✅ Nginx web server active and customized.  
✅ Firewall and security configurations fully operational.

---


