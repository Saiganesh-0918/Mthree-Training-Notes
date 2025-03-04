# Linux Week 3 - Day 2

## **Advanced Linux Commands**

### **Check System Memory Usage**
```sh
free -h   # Displays memory in human-readable format
free -l   # Shows high and low memory status
free -w   # Adds buffer and cache separately
free -g   # Displays memory in gigabytes
```

### **Monitor System Processes**
```sh
ps aux --sort -%mem | head  # Lists processes sorted by memory usage
```

### **Network & IP Configuration**
```sh
ping chatgpt.com  # Checks if the website is reachable
ifconfig          # Displays network interface information
ifconfig eth0     # Shows specific details for eth0 interface
ip addr show      # Displays IP addresses (supports IPv4 & IPv6)
ip -4 addr show   # Shows only IPv4 addresses
ip -6 addr show   # Shows only IPv6 addresses
ip -br addr       # Displays a simplified view of network interfaces
```

## **CPU Stress Testing**
```sh
sudo apt install stress  # Installs the stress testing tool
```

## **Managing Users and Groups**
```sh
sudo adduser username          # Creates a new user
sudo su - username             # Switches to the new user
sudo groupadd c406cohort       # Creates a group
sudo usermod -a -G c406cohort username  # Adds user to the group
```

## **SSH Key Generation & Git Integration**
```sh
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
cd .ssh/
ls -lrt   # List SSH keys
less id_rsa.pub  # View public key
less id_rsa      # View private key
```

## **Cloning a Git Repository**
```sh
git clone git@github.com:username/repository.git
```

## **Installing Jenkins on Linux**
```sh
sudo apt update
sudo apt install fontconfig openjdk-17-jre -y
sudo apt install jenkins -y
```

### **Configuring Jenkins**
```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword  # Retrieve Jenkins admin password
sudo usermod -aG docker jenkins  # Add Jenkins to Docker group
sudo systemctl restart jenkins   # Restart Jenkins to apply changes
```

## **Accessing Jenkins**
Open Jenkins in a browser:
```sh
http://localhost:8080
```

## **Summary**
- Learned **advanced Linux commands** for memory, networking, and process management.
- Practiced **user & group management**.
- Explored **SSH authentication & Git repository cloning**.
- Installed and configured **Jenkins** on Linux.
