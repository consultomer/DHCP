---
marp: true
theme: uncover
class: invert
---
## Dynamic Host Configuration Protocol (DHCP) is a network protocol used to dynamically assign IP addresses and other configuration settings to devices on a network.

---
* Here is a simplified illustration of how DHCP works to allocate IP addresses to clients:

1. Client sends a broadcast message requesting an IP address.
## **DHCP Discover**
![](/images/dhcpdiscover.png)

---
2. DHCP server receives the request and assigns an available IP address to the client along with the subnet mask, default gateway, and DNS server information.
## **DHCP Offer**
![](/images/dhcpoffer.png)

---
3. Client acknowledges the offer and requests the assigned IP address.
## **DHCP Request**
![](/images/dhcprequest.png)

---
4. DHCP server confirms the allocation of IP address to the client.
## **DHCP Acknowledgement**
![](/images/dhcpack.png)

---
5. Client starts using the assigned IP address.
![height:6in](/images/ComDora.webp)
---
This process ensures that every device on the network has a unique IP address and the necessary configuration settings to communicate on the network. The DHCP server keeps track of assigned IP addresses and manages the pool of available addresses to ensure efficient use of IP addresses.

---
# Dynamic Allocation:
A network administrator assigns a range of IP addresses to DHCP, and each client computer on the LAN is configured to request an IP address from the DHCP server during network initialization. The request-and-grant process uses a lease concept with a controllable time period, allowing the DHCP server to reclaim (and then reallocate) IP addresses that are not renewed.

---
# Automatic Allocation:
The DHCP server permanently assigns a free IP address to a requesting client from the range defined by the administrator. This is like dynamic allocation, but the DHCP server keeps a table of past IP address assignments, so that it can preferentially assign to a client the same IP address that the client previously had.

---
# Static Allocation:
The DHCP server allocates an IP address based on a table with MAC address/IP address pairs, which are manually filled in (perhaps by a network administrator). Only requesting clients with a MAC address listed in this table will be allocated an IP address.