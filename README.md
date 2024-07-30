---

# XYZ Company Branch Network

XYZ company, a fast-growing company in Eastern Australia, operates with more than 2 million customers globally. Specializing in the buying and selling of food items, the company is expanding by opening a new branch near the local village Bonalbo. This project entails designing and implementing a network for the new branch, operating independently from the HQ network.

## Network Design Requirements

1. **Hardware**
   - **Router**: 1 CISCO router
   - **Switch**: 1 CISCO switch

2. **Departments**
   - Admin/IT
   - Finance/HR
   - Customer Service/Reception

3. **VLANs**
   - Each department will have its own VLAN.

4. **Wireless Network**
   - Each department requires a wireless network for users.

5. **IP Addressing**
   - Host devices will obtain IPv4 addresses automatically via DHCP.

6. **Inter-Department Communication**
   - Devices in all departments should be able to communicate with each other.

## Network Subneting

### Topology
The network topology consists of a single router connected to a switch. The switch then connects to various access points and department devices. VLANs are configured to segment the network by departments, ensuring each department has its own network space while maintaining the ability to communicate with other departments.

### VLAN Configuration
- **Admin/IT VLAN**: VLAN 10
- **Finance/HR VLAN**: VLAN 20
- **Customer Service/Reception VLAN**: VLAN 30

### IP Addressing
- **Base Network**: 192.168.1.0
- **Admin/IT VLAN**: 192.168.1. 0/26
- **Finance/HR VLAN**: 192.168.1.64/26
- **Customer Service/Reception VLAN**: 192.168.1.128/26

----------------------------
NID = 192.168.1.0 255.255.255.0
Number of departments = Number of subnets = 3
- 2^n >= 3			>>			n= 2
- class C = 255.255.255.0 =>	11111111.11111111.11111111.00000000
Becomes : 11111111.11111111.11111111.11000000
New Subnet : 255.255.255.192
and the block size of 192 is : 64

---------------------------- NID = network ID ; BID = broadcast ID
1st Subnet:
		NID : 192.168.1.0/26
		BID : 192.168.1. 63
		Valid Hosts range : 192.168.1.1 - 192.168.1.62

2nd Subnet:
		NID : 192.168.1.64/26
		BID : 192.168.1. 127
		Valid Hosts range : 192.168.1.65 - 192.168.1.126

3rd Subnet:
		NID : 192.168.1.128/26
		BID : 192.168.1. 191
		Valid Hosts range : 192.168.1.129 - 192.168.1.190

-----------------------------
### DHCP Configuration
- DHCP pools are configured for each VLAN to assign IP addresses automatically to devices.

### Inter-VLAN Routing
- Configured on the router to allow devices in different VLANs to communicate.

## Implementation Instructions

1. **Router Configuration**
   - Configure the router with sub-interfaces for each VLAN.
   - Enable DHCP on each sub-interface.

2. **Switch Configuration**
   - Create VLANs and assign ports to the respective VLANs.
   - Configure trunk ports for communication between the router and switch.

3. **Access Points**
   - Configure access points to broadcast separate SSIDs for each VLAN.

4. **Verification**
   - Verify VLANs are correctly assigned.
   - Ensure devices are receiving IP addresses from the correct DHCP pools.
   - Test inter-VLAN communication.

## Additional Notes

- Ensure the wireless network is secured with appropriate encryption and password protection.
- Monitor network performance and make necessary adjustments to optimize the network.

## Conclusion

This network design will provide a robust and scalable solution for the XYZ company's new branch, meeting all specified requirements and allowing for efficient and secure communication across departments.

---
