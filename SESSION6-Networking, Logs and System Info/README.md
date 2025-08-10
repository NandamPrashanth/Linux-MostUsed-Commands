# SESSION 6 - Networking, Logs and System Info.

In this session we will learn about **Networking**, **Logs**, and **System Information** commands.

# To view network Interfaces  
**ip addr show**    
It will show below details
- ens33 → Interface name
- inet → IPv4 address
- /24 → Subnet mask
- brd → Broadcast address

**To check network Device state**  

**nmcli device status**  

**To test a connectivity**

ping google.com  

**To check firewall status**  
systemctl status firewalld  

firewall-cmd --list-all  

**To open a port permanently**  
firewall-cmd --add-port=8080/tcp --permanent  

Reload firewall to apply permanent changes  
firewall-cmd --reload

**To remove a port**  
firewall-cmd --remove-port=8080/tcp --permanent  

To apply changes reload the firewall  
firewall-cmd --reload  

#  To check logs  

**To view system logs**  
journalctl -xe  

it Shows detailed system logs including errors and warnings.  

**To view general logs**  
tail -n 5 /var/log/messages  

it will display last 5 lines of general logs.  

**To monitor security logs in real time**  
tail -f /var/log/secure  

# System info  

**OS details, kernel version**  
hostnamectl  

**Memory usage info**  
free -h  

**CPU info**  
lscpu  

**OS release info**  
cat /etc/os-release  











