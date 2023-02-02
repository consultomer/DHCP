---
marp: true
theme: uncover
class: invert
---
# **Installing and Configuring DHCP Server**
#### By: Omer

---
# **Scope Of Work**
##### In this document we are going to simulate the installation / configuration and IP reservation of DHCP Server / Client
Following tools were used in this workshop
1. VMware Workstation (as hypervisor) on top of Windows 11. 
1. Ubuntu Server (22.04) (DHCP Server)
1. Ubuntu Server (22.04) (Client server) Host1 and Host 2.

---
# **Diagram For DHCP Lab**
![height:4in](/images/Untitled%20picture.png)

--- 
# **Creating VM of Ubuntu**
#### **1. Select Create New Virtual Machine**
![height:4in](/images/2023-02-01_22h15_26.png)

---
#### **2. Click On Next.**
![height:4in](/images/2023-02-01_22h17_39.png)

---
#### **3. Selecting Image.**
![height:4in](/images/2023-02-01_22h17_52.png)
1. Browse Iso Image.
1. Click On Next.

---
#### **4. Naming Server.**
![height:4in](/images/2023-02-01_22h18_54.png)
1. VM name.
1. VM location.
1. Click Next.

---
#### **5. Storage Allocation.**
![height:4in](/images/2023-02-01_22h19_06.png)
1. Select Size.
1. Click Next.

---
#### **6. Finish.**
![height:4in](/images/2023-02-01_22h19_14.png)
1. Customize Hardware(If Needed).
1. Click On Finish.

---

# **Install DHCP Server**
#### You can install the DHCP Server using the apt command as follow
```
sudo apt install isc-dhcp-server
```
---
# **Backup Configuration File**
Backup Original Configuration file It’s always a good idea to backup original configuration files. In case if something goes wrong.
```
sudo cp /etc/dhcp/dhcpd.conf /etc/dhcp/dhcpd.conf.org
```
![height:2in](/images/2023-02-01_23h27_57.png)

---

## **To Configure the DHPC Server**
The main configuration file of DHCP server is /etc/dhcp/dhcpd.conf
```
sudo vim /etc/dhcp/dhcpd.conf
```

![height:3in](/images/2023-02-01_23h34_15.png)

---


## **According To This Configuration**

1. The Server will hand over the IP Address from the range 192.168.100.20 to 192.168.100.100
1. The default lease time for a client is 10 min(600 seconds) 
1. The maximum lease time is 2 hrs(7200 seconds)

---
# **Backing Up**
Backup Original Configuration file It’s always a good idea to backup original configuration files. In case if something goes wrong.
```
sudo cp /etc/default/isc-dhcp-server /etc/default/isc-dhcp-server.org
```
![height:3in](/images/2023-02-02_00h02_58.png)

---
## **Checking Infterface Name For DHCP**
```
ip a
```
![height:4in](/images/2023-02-01_23h44_24.png)

---
## **Adding Infterface Name For DHCP**
```
sudo vim /etc/default/isc-dhcp-server
```
![height:4in](/images/2023-02-02_00h10_35.png)

---
## **Configuring Firewall**
![height:4in](/images/2023-02-02_00h48_20.png)
```
sudo ufw status
sudo ufw enable
sudo ufw allow 67/udp
sudo ufw allow ssh
```

---
# **Restart the DHCP Server**
Now that changes to the configuration are made, we need to restart the service to enable those changes. 
This can be done using the systemctl command:
```
sudo systemctl restart isc-dhcp-server
```
---
# **Check the status of DHCP Services on DHCP Server**
This can be done using the systemctl command:
```
sudo systemctl status isc-dhcp-server.service
```
An active status indicates that the DHCP Server has successfully picked up the configuration and is ready to hand out IP Addresses.

---
![](/images/2023-02-02_00h53_38.png)

---
# **Check Lease List**
This can be done using the Command:
```
sudo dhcp-lease-list
```
![height:3in](/images/2023-02-02_01h05_05.png)

---
# **Check MAC address Of Host1**
To Check MAC Address use this Command:
```
ip a
``` 
![height:3in](/images/2023-02-02_01h55_10.png)

---
### **Configuring IP Reservation For Host1**
```
sudo vim /etc/dhcp/dhcpd.conf
```
![height:2in](/images/2023-02-02_01h48_53.png)

Now that we have the MAC Address, we can put it in the configuration file:
This will reserve the IP Address 192.168.100.22 for the client with the MAC Address 00:0C:29:95:3B:A6.

---
# **Check Lease List**
This can be done using the Command:
```
sudo dhcp-lease-list
```
![height:3in](/images/2023-02-02_01h58_45.png)

---
# **Troubleshooting**
The DHCP Server writes its logs to the Syslog. If you find that the status of the service is inactive, you should look into /var/log/syslog file. From there on you can search for the specific problem mentioned in the Syslog on the internet.
```
sudo less /var/log/syslog
or
sudo tail -f /var/log/syslog
// for real time update on the log file
```

---
# **Conclusion**
In this article, we learned about DHCP and how to install a DHCP server on an Ubuntu machine. Having a DHCP Server automates the assignment of IP Addresses which is much better than the manual configuration of each client.