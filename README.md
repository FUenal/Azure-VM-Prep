# Azure-VM-Prep

# Configuring and Implementing a Honeypot in Azure



![Banner](https://github.com/FUenal/Azure-VM-Prep/blob/main/assets/1.gif)

### To initiate the commencement of my Azure Honeynet project, the initial step involves configuring the virtual machines (VMs) that will be utilized. These virtual machines, akin to computers in the cloud, will serve as the cornerstone of our honeynet. The following are the procedures we will follow in Microsoft Azure:

1. **Sign in to the Azure portal:** The first step is to log into your Azure account. If you don't have an account yet, **[you'll need to create one!](https://portal.azure.com)**

<details close> 
<summary> 2. Create a virtual machine: </summary>




- Once you're in the Azure portal, navigate to the 'Virtual machines' section. 
  
  ![azure portal](https://github.com/FUenal/Azure-VM-Prep/blob/main/assets/2.png)

  
  
- Click on 'Create', then 'Virtual machine'. This is where we'll set up our new VM!
  
 
  ![VM create](https://github.com/FUenal/Azure-VM-Prep/blob/main/assets/3.png)
  
  </details>
  
  
  <details close> 
<summary> 3. Configure the VM settings: </summary>
  
  - **Subscription and resource group:** We'll select our Azure subscription and resource group (Which is way to group and manage resources in Azure!). For the purpose of the project, I already created created a resource group called ```RG-Cyber-Lab2``` 
  
  - **Virtual Machine Name:** For the purpose of this project, I am going to name this VM, ```Lab-HoneyNet```

  - **Region:** For the purpose of this project, I am going to choose the region, ```(US) East US 2```
  
  - **Availability Options:** Being that the only purpose of this machine will be to act as a Honeypot, we do not require any form of availability, so I selected ```No infrastructure redundancy required```

  - **Image:** Select ```Windows 10 Pro, version 21H2 - x64 Gen2```
  
  ![VM create](https://github.com/FUenal/Azure-VM-Prep/blob/main/assets/4.png)
  
  - **Networking**: When creating the virtual network, we will be leaving it to the default settings. For the purpose of this lab, I called mine ```Lab-VNet```.
  
  ![netowkr](https://github.com/FUenal/Azure-VM-Prep/blob/main/assets/5.png)


  </details>


<details close> 
<summary> 4. NSG/Inbound Security Rule Configuration: </summary>
 
  - **Navigate to the Network Security Group (NSG):** In the Azure portal, search for 'Network Security Groups' in the search bar at the top. Once there, select the NSG associated with your virtual machine.
  
  - **Create an inbound security rule:** Inside the NSG, you'll find a section for 'Inbound security rules'. This is where we control what kind of traffic is allowed to reach our VM. Click on 'Add' to create a new rule.
  - **Configure the rule:** We'll be prompted to input some details about our new rule.
  
  - **Source:** This defines where the incoming traffic is coming from. We can set this to ```Any``` to allow traffic from any location.
  
  - **Source port ranges:** This specifies the ports on the source (the computer initiating the connection) that are allowed. Again, we can set this to ```*``` or ```Any``` to allow all ports.

  - **Destination:** This defines where the traffic is going to. Since we want the traffic to reach our VM, we can set this to ```Any```.
  
  - **Destination port ranges:** This specifies the ports on our VM that are allowed to receive traffic. We can set this to ```*``` or ```Any``` to open all ports.
  
  - **Priority:** Setting priorities in Network Security Groups (NSGs) is an essential step. The priority determines the order in which rules are applied. Rules with lower priority numbers are processed before rules with higher priority numbers because the lower the number, the higher the priority. For the purpose of this lab, I set the priority to ```300``` to ensure that this honeypot functions as intended!

  - **Action:** We'll set this to ```Allow```, which means that traffic matching this rule will be allowed to reach our VM. 
  
 ![NSG](https://github.com/FUenal/Azure-VM-Prep/blob/main/assets/6.png)

  
  - **Review & Create:** After i've input and configured all the details we need for this inbound rule, click 'Add' to create the rule. e
 
 
 
 
 
 
 
 
 
</details>

# Conclusion

### Through the establishment of our VMs and the implementation of open inbound security rules, we are essentially allowing unrestricted access through the front door of our VM. Typically, such a practice is not advisable in a real production environment, as it exposes the system to significant vulnerability against attacks. Nevertheless, within the context of our honeynet, this is precisely the desired approach!

### This enables us to draw in potential attackers and monitor their behavior within a regulated setting.
 
