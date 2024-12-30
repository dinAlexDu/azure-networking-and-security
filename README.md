# Azure Networking and Security

This project demonstrates how to set up and secure virtual networks in Azure. It includes creating Virtual Networks (VNets), configuring subnets, Network Security Groups (NSGs), peering two VNets, and testing connectivity using Virtual Machines (VMs). Additionally, it highlights the use of Azure Bastion for secure VM access.

## Project Objectives
  - Set up two Virtual Networks (VNet1 and VNet2) with appropriate subnets.
  - Configure Network Security Groups (NSGs) to control inbound and outbound traffic.  
  - Peer VNet1 and VNet2 to enable cross-network communication.
  - Deploy and test Virtual Machines (VMs) within the VNets.
  - Use Azure Bastion for secure and public IP-independent access to the VMs.


## Steps Implemented

1. **Create Virtual Networks**
  - Set up VNet1 and VNet2 with custom CIDR ranges.
  - Configure subnets, including an AzureBastionSubnet.

  - VNet1:
     - Address space: 10.1.0.0/16
     - Subnet1: 10.1.0.0/24 (Default subnet)
     - AzureBastionSubnet: 10.1.1.0/24
   - VNet2:
     - Address space: 10.2.0.0/16
     - Subnet2: 10.2.0.0/24 (Default subnet)
  
2. **Configure Network Security Groups (NSGs)**
  - Create NSGs for both VNets.
  - Set rules to allow ICMP (Ping) and SSH traffic.

   - NSG-VNet1:
     - Allow SSH (Port 22) inbound from any source.
     - Allow ICMP (Ping) inbound for troubleshooting.
   - NSG-VNet2:
     - Allow SSH (Port 22) inbound from any source.
     - Allow ICMP (Ping) inbound for troubleshooting.
 
3. **Peer Virtual Networks**
  - Establish bidirectional communication between VNet1 and VNet2.

   - Peering from VNet1 to VNet2:
     - Enabled Allow Gateway Transit.
   - Peering from VNet2 to VNet1:
     - Enabled Use Remote Gateways.
    
4. **Deploy Virtual Machines**
  - Create Ubuntu VMs in each VNet for connectivity testing.

   - VM1 in VNet1:
     - Private IP: 10.1.0.4
     - NSG: Associated with NSG-VNet1
     - OS: Ubuntu 20.04 LTS
   - VM2 in VNet2:
     - Private IP: 10.2.0.4
     - NSG: Associated with NSG-VNet2
     - OS: Ubuntu 20.04 LTS

5. **Test Connectivity**
  - Validate communication between VMs across VNets using ping and ssh.

    - From VM1 in VNet1, ping VM2 in VNet2 using:
     ```bash
     ping 10.2.0.4
     ```
   - From VM2 in VNet2, ping VM1 in VNet1 using:
     ```bash
     ping 10.1.0.4
     ```
    
6. **Deploy Azure Bastion**
  - Configure Azure Bastion for secure VM management without public IPs.

    - Deployment in VNet1:
     - Associated with AzureBastionSubnet.
     - Tested SSH access to VM1 and VM2 without using public IPs.

### Screenshots

1. **Virtual Network Creation**  
   ![Virtual Network Creation](./images/virtual-network-creation.png)

2. **Subnet Configuration**  
   ![Subnet Configuration](./images/subnets-configuration.png)

3. **NSG Configuration**  
   ![NSG Configuration](./images/nsg-configuration.png)

4. **VNet Peering Configuration**  
   ![VNet Peering Configuration](./images/vnet-peering-configuration.png)

5. **Ping Test Between VMs**  
   ![Ping Test Between VMs](./images/ping-test-between-vms.png)

6. **Azure Bastion Deployment**  
   ![Azure Bastion Deployment](./images/azure-bastion-creation.png)

7. **Azure Bastion Connection**  
   - Part 1: ![Azure Bastion Connection 1](./images/azure-bastion-connection-1.png)  
   - Part 2: ![Azure Bastion Connection 2](./images/azure-bastion-connection-2.png)

8. **Virtual Machine Overviews**  
   - VM in VNet1: ![VM in VNet1](./images/virtual-machine-1-overview.png)  
   - VM in VNet2: ![VM in VNet2](./images/virtual-machine-2-overview.png)


## Technologies Used
  - Azure Virtual Networks (VNets) for network segmentation.
  - Network Security Groups (NSGs) for traffic filtering.
  - Azure Bastion for secure VM management.
  - Ubuntu Linux VMs for testing network connectivity.

---

## Steps to Reproduce

1. Clone this repository:
   git clone https://github.com/dinAlexDu/azure-networking-and-security.git
   cd azure-networking-and-security

2. Follow the Azure Virtual Network Documentation:
   https://learn.microsoft.com/en-us/azure/virtual-network/

3. Configure subnets and NSGs as per the project steps.

4. Test connectivity between VMs and deploy Azure Bastion for secure access.

---

## Useful Links

- Azure Virtual Network Documentation: https://learn.microsoft.com/en-us/azure/virtual-network/
- Azure Bastion Documentation: https://learn.microsoft.com/en-us/azure/bastion/
- Network Security Groups Documentation: https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Contributions
Contributions are welcome! Please fork this repository and submit a pull request with your improvements.


