
# Configuring and Implementing A Honeypot in Azure




![Banner](https://i.imgur.com/laopbj3.gif)

### To initiate my Azure Honeynet project, the initial step involves configuring the virtual machines (VMs) that will be utilized. These VMs serve as cloud-based computers and will serve as the fundamental building blocks of our honeynet. The following are the steps we will undertake in Microsoft Azure to set up the environment:

1. **Sign in to the Azure portal:** The first step is to log into your Azure account. If you don't have an account yet, **[you'll need to create one!](https://portal.azure.com)**

<details close> 
<summary> 2. Create a virtual machine: </summary>




- Once you have accessed the Azure portal, proceed to the 'Virtual machines' section by navigating through the interface.
  
  ![azure portal](https://i.imgur.com/8800xwE.png)

  
  
- Select the 'Create' option, followed by 'Azure Virtual machine' to initiate the setup process for our new VM.
  
 
  ![VM create](https://i.imgur.com/k7O7IfJ.png)
  
  </details>
  
  
  <details close> 
<summary> 3. Configure the VM settings: </summary>
  
  - **Subscription and resource group:** We'll select our Azure subscription and resource group (Which is way to group and manage resources in Azure!). For the purpose of the project, I already created created a resource group called ```RG-Cyber-Lab2``` 
  
  - **Virtual Machine Name:** In alignment with this project, I will assign the name "Lab-HoneyNet" to this particular VM.

  - **Region:** In alignment with this project, I am going to choose the region, ```(US) East US 2```
  
  - **Availability Options:** Considering that this machine is solely intended to function as a Honeypot, there is no need for any kind of availability. Therefore, I have chosen the option "No infrastructure redundancy required."

  - **Image:** Select ```Windows 10 Pro, version 21H2 - x64 Gen2```
  
  ![VM create](https://i.imgur.com/qNxTNbe.png)
  
  - **Networking**: When setting up the virtual network, we will retain the default configurations. In this lab, I have named the virtual network "Lab-VNet" to suit our objectives..
  
  ![netowkr](https://i.imgur.com/sQWcUgD.png)


  </details>


<details close> 
<summary> 4. NSG/Inbound Security Rule Configuration: </summary>
 
  - To access the Network Security Group (NSG), follow these steps in the Azure portal: Use the search bar at the top of the portal to search for 'Network Security Groups'. Locate and select the NSG that is associated with your virtual machine.
  
  - To create an inbound security rule, navigate to the 'Inbound security rules' section within the NSG. This section allows us to manage the type of traffic that can access our VM. Click on the 'Add' button to generate a new rule.
    
  - Configure the rule by providing the necessary details when prompted.
  
  - Source: This defines where the incoming traffic is coming from. We can set this to ```Any``` to allow traffic from any location.
  
  - Source port ranges: This specifies the allowed ports on the source (the computer initiating the connection). Once again, we have the option to set this to  ```*``` or ```Any``` to allow all ports.

  - Destination: This defines the destination for the traffic. Since we want the traffic to reach our VM, we can set this as ```Any```.
  
  - Destination port ranges:** This determines the allowed ports on our VM to receive incoming traffic. To open all ports, we can set this as ```*``` or ```Any```.
  
  - Priority: Establishing priorities in Network Security Groups (NSGs) is a crucial step. The priority assigned to each rule determines the sequence in which they are applied. Rules with lower priority numbers take precedence over those with higher priority numbers, as lower numbers indicate higher priority. In this lab, I have assigned a priority of ```300``` to ensure the proper functioning of this honeypot.

  - Action: We will configure this as ```Allow```, indicating that traffic conforming to this rule will be permitted to reach our VM.
      
 ![NSG](https://i.imgur.com/Y15P2EI.png)

  
  - Review & Create: Once you have entered and configured all the necessary details for this inbound rule, click on 'Add' to create the rule successfully.
 
 
 
 
 

### By creating our VMs and allowing open inbound security rules, we are essentially leaving the front door of our VM wide open. This is typically not recommended in a real production environment as it would make the system highly vulnerable to attacks. However, in the context of our honeynet, this is precisely the approach we want to take.

### This approach enables us to draw the attention of potential attackers and carefully observe their actions within a controlled environment.
 
