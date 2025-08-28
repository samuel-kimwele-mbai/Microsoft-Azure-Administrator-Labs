This lab is the first of three labs that focuses on virtual networking. 
In this lab, I learnt the basics of virtual networking and subnetting. I learnt how to protect network with network security groups and application security groups. I also learnt about DNS zones and records.

This lab has four tasks:
Task 1: Create a virtual network with subnets using the portal.
Task 2: Create a virtual network and subnets using a template.
Task 3: Create and configure communication between an Application Security Group and a Network Security Group.
Task 4: Configure public and private Azure DNS zones.

Task 1: Create a virtual network with subnets using the portal.
The organization plans a large amount of growth for core services. In this task, I created the virtual network and the associated subnets to accommodate the existing resources and planned growth. 

1. Sign in to the Azure portal - https://portal.azure.com. Search for and select Virtual Networks and Select Create on the Virtual networks page.

2. Complete the Basics tab for the CoreServicesVnet.
<img width="792" height="586" alt="image" src="https://github.com/user-attachments/assets/22b4f681-3c87-4c5e-9fdb-af4fadc47b73" />

The security tab has the following, I left it with the default settings:
<img width="745" height="594" alt="image" src="https://github.com/user-attachments/assets/715137c7-df23-4b7d-9363-3a1cb6a4e022" />

3. Move to the IP Addresses tab.
<img width="801" height="525" alt="image" src="https://github.com/user-attachments/assets/1cef8296-80e1-4de3-a743-0a337db81eed" />

4. Select + Add a subnet. Complete the name and address information for each subnet. Be sure to select Add for each new subnet. Be sure to delete the default subnet - either before or after creating the other 
subnets.
<img width="525" height="669" alt="image" src="https://github.com/user-attachments/assets/4a9c0acc-b9b6-4a24-8100-5463bdd9fb49" />

<img width="520" height="724" alt="image" src="https://github.com/user-attachments/assets/af3b7092-2c7d-4d2b-8094-dc211993816c" />


Note: Every virtual network must have at least one subnet. Reminder that five IP addresses will always be reserved, so consider that in your planning.

5. To finish creating the CoreServicesVnet and its associated subnets, select Review + create. Verify your configuration passed validation, and then select Create. Wait for the virtual network to deploy and 
then select Go to resource.

6. In the Automation section, select Export template, and then wait for the template to be generated. Download the template. Navigate on the local machine to the Downloads folder and Extract all the files in 
the downloaded zip file.

- Before proceeding, ensure you have the template.json file. You will use this template to create the ManufacturingVnet in the next task.



Task 2: Create a virtual network and subnets using a template
In this task, I created the ManufacturingVnet virtual network and associated subnets. The organization anticipates growth for the manufacturing offices so the subnets are sized for the expected growth. For 
this task, I used a template to create the resources.

- Locate the template.json file exported in the previous task. 
- Edit the file using the editor of your choice(I used visual studio code). Many editors have a change all occurrences feature. 

Make changes for the ManufacturingVnet virtual network

1. Replace all occurrences of CoreServicesVnet with ManufacturingVnet.
<img width="1382" height="791" alt="image" src="https://github.com/user-attachments/assets/ae3fc8e6-1cf0-4c83-aedc-17d5f767861d" />

Replace all occurrences of 10.20.0.0 with 10.30.0.0.
<img width="1259" height="792" alt="image" src="https://github.com/user-attachments/assets/d2981f80-c040-4846-9d07-63570e7deea5" />

2. Make changes for the ManufacturingVnet subnets
3. Change all occurrences of SharedServicesSubnet to SensorSubnet1.
4. Change all occurrences of 10.20.10.0/24 to 10.30.20.0/24.
5. Change all occurrences of DatabaseSubnet to SensorSubnet2.
6. Change all occurrences of 10.20.20.0/24 to 10.30.21.0/24.

Be sure to Save your changes.


- Make changes to the parameters file
1. Replace the one occurrence of CoreServicesVnet with ManufacturingVnet.
2. Save your changes.


Deploy the custom template
1. In the portal, search for and select Deploy a custom template. Then Select Build your own template in the editor and then Load file and Select the template.json file with your Manufacturing changes, then 
select Save.
<img width="1417" height="696" alt="image" src="https://github.com/user-attachments/assets/bec374be-d00e-4c4e-98ed-d151f86560d9" />

2. Ensure your resource group, az104-rg4 is selected. Select Review + create and then Create. Wait for the template to deploy, then confirm (in the portal) the Manufacturing virtual network and subnets were 
created.
<img width="1424" height="490" alt="image" src="https://github.com/user-attachments/assets/044e7cfe-0f0c-4370-b707-c535dd317ff7" />



Task 3: Create and configure communication between an Application Security Group and a Network Security Group

In this task, I will create an Application Security Group and a Network Security Group. The NSG will have an inbound security rule that allows traffic from the ASG. The NSG will also have an outbound rule that 
denies access to the internet.

Create the Application Security Group (ASG)

1. In the Azure portal, search for and select Application security groups. Click Create and provide the basic information.
<img width="1438" height="425" alt="image" src="https://github.com/user-attachments/assets/ade2e061-bc80-4f32-bc93-74de7ff3a852" />

2. Click Review + create and then after the validation click Create.
<img width="1431" height="632" alt="image" src="https://github.com/user-attachments/assets/5aec4fb3-9f34-412f-92c6-3bae5187fb71" />

Note: At this point, you would associate the ASG with virtual machine(s). These machines will be affected by the inbound NSG rule you create in the next task.

Create the Network Security Group and associate it with CoreServicesVnet
