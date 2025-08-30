Lab introduction
In this lab, you create and compare virtual machines to virtual machine scale sets. You learn how to create, configure and resize a 
single virtual machine. You learn how to create a virtual machine scale set and configure autoscaling.

Lab scenario
Your organization wants to explore deploying and configuring Azure virtual machines. First, you implement an Azure virtual machine with manual scaling. Next, you implement a
 Virtual Machine Scale Set and explore autoscaling.

 This lab has these 6 tasks:
Task 1: Deploy zone-resilient Azure virtual machines by using the Azure portal.
Task 2: Manage compute and storage scaling for virtual machines.
Task 3: Create and configure Azure Virtual Machine Scale Sets.
Task 4: Scale Azure Virtual Machine Scale Sets.
Task 5: Create a virtual machine using Azure PowerShell (optional 1).
Task 6: Create a virtual machine using the CLI (optional 2).

**Task 1: Deploy zone-resilient Azure virtual machines by using the Azure portal.**
In this task, you will deploy two Azure virtual machines into different availability zones by using the Azure portal. Availability zones offer the highest level of uptime SLA for virtual machines at 99.99%. To achieve this SLA, you must deploy at least two virtual machines across different availability zones.

Sign in to the Azure portal - https://portal.azure.com.

Search for and select Virtual machines, on the Virtual machines blade, click + Create, and then select in the drop-down Azure virtual machine. Notice your other choices.

On the Basics tab, in the Availability zone drop down menu, place a checkmark next to Zone 2. This should select both Zone 1 and Zone 2.

Note: This will deploy two virtual machines in the selected region, one in each zone. You achieve the 99.99% uptime SLA because you have at least two VMs distributed across at least two zones. In the scenario where you might only need one VM, it is a best practice to still deploy the VM to another zone.

On the Basics tab, continue completing the configuration:

<img width="1090" height="347" alt="image" src="https://github.com/user-attachments/assets/443f181e-9dcf-4983-addc-ebb12f7263ee" />
<img width="1080" height="352" alt="image" src="https://github.com/user-attachments/assets/76e47439-6c2a-4e6b-989d-992decdd224b" />
<img width="1079" height="346" alt="image" src="https://github.com/user-attachments/assets/a3cc0491-866e-4462-b3ff-e96552edc0c2" />
<img width="1092" height="356" alt="image" src="https://github.com/user-attachments/assets/0624b598-9c9e-4532-b953-ec7453ca7444" />


Click Next : Disks > , specify the following settings (leave others with their default values):
<img width="1091" height="344" alt="image" src="https://github.com/user-attachments/assets/508759eb-425f-4069-9f43-20bd7ccdf09d" />

Click Next : Networking > take the defaults but do not provide a load balancer.

Setting	Value
Delete public IP and NIC when VM is deleted	Checked
Load balancing options	None


Click Next : Management > and specify the following settings (leave others with their default values):

Setting	Value
Patch orchestration options	Azure orchestrated


Click Next : Monitoring > and specify the following settings (leave others with their default values):

<img width="1094" height="349" alt="image" src="https://github.com/user-attachments/assets/c2ab919e-acfe-4eb2-8461-692abb8ba300" />

Click Next : Advanced >, take the defaults, then click Review + Create.

After the validation, click Create.

Note: Notice as the virtual machine deploys the NIC, disk, and public IP address (if configured) are independently created and managed resources.

Wait for the deployment to complete, then select Go to resource
<img width="1091" height="610" alt="image" src="https://github.com/user-attachments/assets/ec25d437-582f-4eb1-b118-360cc0c01f86" />


**Task 2: Manage compute and storage scaling for virtual machines**
In this task, you will scale a virtual machine by adjusting its size to a different SKU. Azure provides flexibility in VM size selection so that you can adjust a VM for 
periods of time if it needs more (or less) compute and memory allocated. This concept is extended to disks, where you can modify the performance of the disk, or increase the allocated capacity.

On the az104-vm1 virtual machine, in the Availability + scale blade, select Size.

Set the virtual machine size to D2ds_v4 and click Resize. When prompted, confirm the change.

Note: If the D2ds_v4 size is not available, skip to step 3. This step does not need to be completed in order to complete the rest of the lab.
<img width="1096" height="608" alt="image" src="https://github.com/user-attachments/assets/85e803fd-b1d2-43e3-955a-0a256f679512" />

In the Settings area, select Disks.

Under Data disks select + Create and attach a new disk. Configure the settings (leave other settings at their default values).
<img width="1040" height="573" alt="image" src="https://github.com/user-attachments/assets/e030b503-3090-42f5-aab9-07c14e322f8c" />

Click Apply.

After the disk has been created, click Detach (if necessary, scroll to the right to view the detach icon), and then click Apply.

Note: Detaching removes the disk from the VM but keeps it in storage for later use.

Search for and select Disks. From the list of disks, select the vm1-disk1 object.

Note: The Overview blade also provides performance and usage information for the disk.
<img width="1088" height="610" alt="image" src="https://github.com/user-attachments/assets/bae8b812-86e0-48bb-9304-5401e51ca8f1" />

In the Settings blade, select Size + performance.

Set the storage type to Standard SSD, and then click Save.
<img width="1088" height="607" alt="image" src="https://github.com/user-attachments/assets/1e278cc8-3f4b-4b24-88c9-c2d8a3b9b8a5" />

Navigate back to the az104-vm1 virtual machine and select Disks.

In the Data disk section, select Attach existing disks.

In the Disk name drop-down, select VM1-DISK1.

Verify the disk is now Standard SSD.

Select Apply to save your changes.

Note: You have now created a virtual machine, scaled the SKU and the data disk size. In the next task we use Virtual Machine Scale Sets to automate the scaling process.
<img width="1090" height="608" alt="image" src="https://github.com/user-attachments/assets/b8b29cb7-21e2-42ee-a2fc-3ae97da403d2" />


**Task 3: Create and configure Azure Virtual Machine Scale Sets**
In this task, you will deploy an Azure virtual machine scale set across availability zones. VM Scale Sets reduce the administrative overhead of automation by enabling you to configure 
metrics or conditions that allow the scale set to horizontally scale, scale in or scale out.

In the Azure portal, search for and select Virtual machine scale sets and, on the Virtual machine scale sets blade, click + Create.

On the Basics tab of the Create a virtual machine scale set blade, specify the following settings (leave others with their default values) and click Next : Spot >:
<img width="1087" height="486" alt="image" src="https://github.com/user-attachments/assets/6f2bd159-b425-4952-8bbd-f9b23532c203" />
<img width="1074" height="425" alt="image" src="https://github.com/user-attachments/assets/2d4a4cc4-e98d-4738-95ca-b9b2dab9586d" />
<img width="1100" height="384" alt="image" src="https://github.com/user-attachments/assets/9283caa5-dbd6-4e73-94b9-5004c66d0fd4" />



On the Spot tab, accept the defaults and select Next : Disks >.

On the Disks tab, accept the default values and click Next : Networking >.

On the Networking page, select Edit virtual network link. Make a few changes. When finished, select OK.
<img width="1079" height="625" alt="image" src="https://github.com/user-attachments/assets/e7ab56ea-a501-45a9-8f4d-1e57ea94756e" />

In the Networking tab, click the Edit network interface icon to the right of the network interface entry.
<img width="1090" height="610" alt="image" src="https://github.com/user-attachments/assets/75d1db4e-6526-4c72-a5c5-d1e8042f0956" />

For NIC network security group section, select Advanced and then click Create new under the Configure network security group drop-down list.
<img width="1101" height="530" alt="image" src="https://github.com/user-attachments/assets/b52dda40-1476-49fe-85f3-067eb28e3793" />


On the Create network security group blade, specify the following settings (leave others with their default values):

Setting	Value
Name	vmss1-nsg

In the Networking tab, under the Load balancing section, specify the following (leave others with their default values).
On the Create a load balancer page, specify the load balancer name and take the defaults. Click Create when you are done then Next : Management >.
<img width="1103" height="613" alt="image" src="https://github.com/user-attachments/assets/4d05e3a0-0008-4a30-a301-835da7d2fc97" />

On the Management tab, specify the following settings (leave others with their default values):
<img width="1091" height="608" alt="image" src="https://github.com/user-attachments/assets/3462d1f7-9fee-4459-96f3-6ae66f111d42" />

On the Review + create tab, ensure that the validation passed and click Create.

**Task 4: Scale Azure Virtual Machine Scale Sets**
In this task, you scale the virtual machine scale set using a custom scale rule.

Select Go to resource or search for and select the vmss1 scale set.

Choose Availability + Scale from the left side menu, then choose Scaling.
<img width="1097" height="567" alt="image" src="https://github.com/user-attachments/assets/478d870e-dc5c-42f0-a0ef-b492bb1351b3" />
Did you know? You can Manual scale or Custom autoscale. In scale sets with a small number of VM instances, increasing or decreasing the instance count (Manual scale) may be best. In scale sets with a large number of 
VM instances, scaling based on metrics (Custom autoscale) may be more appropriate.

Select Custom autoscale. Then change the Scale mode to Scale based on metric. And then select Add a rule.
Let's create a rule that automatically increases the number of VM instances. This rule scales out when the average CPU load is greater than 70% over a 10-minute period. When the rule triggers, the number of VM instances
 is increased by 50%.
 <img width="1099" height="608" alt="image" src="https://github.com/user-attachments/assets/45729dc5-a749-42c3-9ca1-d98b267d7e95" />
<img width="1099" height="611" alt="image" src="https://github.com/user-attachments/assets/7e89844e-0037-42b8-89bf-4c995a3e9c98" />
During evenings or weekends, demand may decrease so it is important to create a scale in rule.

Let's create a rule that decreases the number of VM instances in a scale set. The number of instances should decrease when the average CPU load drops below 30% over a 10-minute period. When the rule triggers, the number of VM instances is decreased by 20%.

Select Add a rule, adjust the settings, then select Add.

Setting	Value
Operator	Less than
Threshold	30
Operation	decrease percentage by (review your other choices)
Percentage	50

Set the instance limits

When your autoscale rules are applied, instance limits make sure that you do not scale out beyond the maximum number of instances or scale in beyond the minimum number of instances.

Instance limits are shown on the Scaling page after the rules.

Setting	Value
Minimum	2
Maximum	10
Default	2



Task 5: Create a virtual machine using Azure PowerShell (option 1)
Use the icon (top right) to launch a Cloud Shell session. Alternately, navigate directly to https://shell.azure.com.

Be sure to select PowerShell. If necessary, configure the shell storage.

Run the following command to create a virtual machine. When prompted, provide a username and password for the VM. While you wait check out the New-AzVM command reference for all the parameters associated 
with creating a virtual machine.

New-AzVm `
-ResourceGroupName 'az104-rg8-lod54225815' `
-Name 'myPSVM' `
-Location 'eastus2' `
-Image 'Win2019Datacenter' `
-Zone '1' `
-Size 'Standard_D2s_v3' `
-Credential (Get-Credential)

Once the command completes, use Get-AzVM to list the virtual machines in your resource group.
Get-AzVM `
-ResourceGroupName 'az104-rg8-lod54225815' `
-Status







Key takeaways
Congratulations on completing the lab. Here are the main takeaways for this lab.

Azure virtual machines are on-demand, scalable computing resources.
Azure virtual machines provide both vertical and horizontal scaling options.
Configuring Azure virtual machines includes choosing an operating system, size, storage and networking settings.
Azure Virtual Machine Scale Sets let you create and manage a group of load balanced VMs.
The virtual machines in a Virtual Machine Scale Set are created from the same image and configuration.
In a Virtual Machine Scale Set the number of VM instances can automatically increase or decrease in response to demand or a defined schedule.
