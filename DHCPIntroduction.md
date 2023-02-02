---
marp: true
theme: uncover
class: invert
---
# **Introduction To DHCP Server**
#### By: Omer

---
DHCP stands for Dynamic Host Configuration Protocol is a network protocol used to dynamically assign IP addresses and other configuration settings to devices on a network.

---
1. How DHCP works to allocate IP addresses to clients:

![height:6in](/images/DHCP.drawio.png)

---
1. Client sends a broadcast message requesting an IP address.
1. DHCP server receives the request and assigns an available IP address to the client.
1. Client acknowledges the offer and requests the assigned IP address.
1. DHCP server confirms the allocation of IP address to the client.
* These steps are known as DORA

---
# **1. Discover**

![](/images/DHCPDiscover.png)

---
# **2. Offer**

![](/images/DHCPOffer.png)

---
# **3. Request**

![](/images/DHCPRequest.png)

---
# **4. Acknowledgement**

![](/images/DHCPAck.png)


---
This process ensures that every device on the network has a unique IP address and the necessary configuration settings to communicate on the network. The DHCP server keeps track of assigned IP addresses and manages the pool of available addresses to ensure efficient use of IP addresses.



---
# **Types of Allocations**
1. Dynamic Allocation 
1. Automatic Allocation
1. Static Allocation

---
# **Dynamic Allocation:**
An administrator assigns a range of IP addresses to DHCP, and each client computer on the LAN is configured to request an IP address from the DHCP server during network initialization. 

---
# **Automatic Allocation:**
The DHCP server permanently assigns a free IP address to a requesting client from the range defined by the administrator. This is like dynamic allocation, but the DHCP server keeps a table of past IP address assignments, so that it can preferentially assign to a client the same IP address that the client previously had.

---
# **Static Allocation:**
The DHCP server allocates an IP address based on a table with MAC address/IP address pairs, which are manually filled in (perhaps by a network administrator). Only requesting clients with a MAC address listed in this table will be allocated an IP address.