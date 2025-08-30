Lab introduction
In this lab you explore communication between virtual networks. You implement virtual network peering and test connections. You will also create a custom route.

This lab has 5 tasks:
Task 1: Create a virtual machine in a virtual network.
Task 2: Create a virtual machine in a different virtual network.
Task 3: Use Network Watcher to test the connection between virtual machines.
Task 4: Configure virtual network peerings between different virtual networks.
Task 5: Use Azure PowerShell to test the connection between virtual machines.
Task 6: Create a custom route.


Task 1: Create a core services virtual machine and virtual network

Sign in to the Azure portal - https://portal.azure.com.

Search for and select Virtual Machines.

From the virtual machines page, select Create then select Azure Virtual Machine.

On the Basics tab, use the following information to complete the form, and then select Next: Disks >. For any setting not specified, leave the default value.

<img width="997" height="540" alt="image" src="https://github.com/user-attachments/assets/4e28d934-c2a5-43b6-883b-9c6832221466" />
<img width="995" height="551" alt="image" src="https://github.com/user-attachments/assets/f88629f8-5d1a-4d4d-af90-ba8dfc881621" />
<img width="991" height="554" alt="image" src="https://github.com/user-attachments/assets/9e372d72-b739-4613-82ae-40fe2e7df56a" />

On the Disks tab take the defaults and then select Next: Networking >.

On the Networking tab, for Virtual network, select Create new.

Use the following information to configure the virtual network, and then select OK. If necessary, remove or replace the existing information.

<img width="1103" height="613" alt="image" src="https://github.com/user-attachments/assets/6930f78b-e847-4555-9dcc-a33c0a21886a" />

Select the Monitoring tab. For Boot Diagnostics, select Disable.

<img width="1073" height="488" alt="image" src="https://github.com/user-attachments/assets/df35a443-b1d3-429e-8589-c91cff3c6318" />


Select Review + Create, and then select Create.

**Task 2: Create a virtual machine in a different virtual network**
In this task, you create a manufacturing services virtual network with a virtual machine.

From the Azure portal, search for and navigate to Virtual Machines.

From the virtual machines page, select Create then select Azure Virtual Machine.

On the Basics tab, use the following information to complete the form, and then select Next: Disks >. For any setting not specified, leave the default value.

<img width="1090" height="403" alt="image" src="https://github.com/user-attachments/assets/53cf3a8a-8810-4720-8436-24ce3d9aeef1" />
<img width="1095" height="390" alt="image" src="https://github.com/user-attachments/assets/dea5e9ac-029c-4022-87e8-728d3a9174d2" />
<img width="1099" height="484" alt="image" src="https://github.com/user-attachments/assets/80ac5f1f-51f6-4f85-a8b3-ae1248a6f471" />

On the Disks tab take the defaults and then select Next: Networking >.

On the Networking tab, for Virtual network, select Create new.

Use the following information to configure the virtual network, and then select OK. If necessary, remove or replace the existing address range.
<img width="946" height="610" alt="image" src="https://github.com/user-attachments/assets/c5b9bd79-d91f-4d21-af56-919e3c0315bf" />

Select the Monitoring tab. For Boot Diagnostics, select Disable.

Select Review + Create, and then select Create.
<img width="1094" height="418" alt="image" src="https://github.com/user-attachments/assets/86e83e7c-0152-43f8-ae64-7b4db9e899bf" />

**Task 3: Use Network Watcher to test the connection between virtual machines**
In this task, you verify that resources in peered virtual networks can communicate with each other. Network Watcher will be used to test the connection. Before continuing, ensure both virtual machines have been deployed and are running.

From the Azure portal, search for and select Network Watcher.

From Network Watcher, in the Network diagnostic tools menu, select Connection troubleshoot.

Use the following information to complete the fields on the Connection troubleshoot page.
<img width="1084" height="499" alt="image" src="https://github.com/user-attachments/assets/e8cab1a5-4cc5-4d12-a9be-17e18081694c" />

<img width="1096" height="392" alt="image" src="https://github.com/user-attachments/assets/5e29dba9-2f7a-412f-b31b-b1f2e00cf492" />

Select Run diagnostic tests.
 the Connectivity test shows UnReachable. This makes sense because the virtual machines are in different virtual networks.
 <img width="1017" height="440" alt="image" src="https://github.com/user-attachments/assets/94520acb-1926-485f-977e-154b6edd2cf8" />


**Task 4: Configure virtual network peerings between virtual networks**
In this task, you create a virtual network peering to enable communications between resources in the virtual networks.

In the Azure portal, select the CoreServicesVnet virtual network.

In CoreServicesVnet, under Settings, select Peerings.

On CoreServicesVnet, under Peerings, select + Add. If not specified, take the default.

<img width="1103" height="573" alt="image" src="https://github.com/user-attachments/assets/335079c0-0eb3-4eaa-b5c9-f09985a69bac" />
<img width="1097" height="406" alt="image" src="https://github.com/user-attachments/assets/8fc702f8-f50d-494c-9dad-6c510bc2df0d" />
<img width="1091" height="470" alt="image" src="https://github.com/user-attachments/assets/9ae5b314-115d-44dd-baf5-9134fa7b8a50" />


In CoreServicesVnet, under Peerings, verify that the CoreServicesVnet-to-ManufacturingVnet peering is listed. Refresh the page to ensure the Peering status is Connected.

<img width="803" height="260" alt="image" src="https://github.com/user-attachments/assets/70362271-6775-443a-a347-9bbe27a5f947" />

Switch to the ManufacturingVnet and verify the ManufacturingVnet-to-CoreServicesVnet peering is listed. Ensure the Peering status is Connected. You may need to Refresh the page.
<img width="789" height="264" alt="image" src="https://github.com/user-attachments/assets/9a819ffc-650e-44e3-bedd-f4c228f58002" />


**Task 5: Use Azure PowerShell to test the connection between virtual machines**
In this task, you retest the connection between the virtual machines in different virtual networks.

Verify the private IP address of the CoreServicesVM
From the Azure portal, search for and select the CoreServicesVM virtual machine.

On the Overview blade, in the Networking section, record the Private IP address of the machine. You need this information to test the connection.

<img width="1093" height="611" alt="image" src="https://github.com/user-attachments/assets/7ce5cdf3-8ac5-42e5-8be5-cd162ce6e40c" />


Test the connection to the CoreServicesVM from the ManufacturingVM.
Did you know? There are many ways to check connections. In this task, you use Run command. You could also continue to use Network Watcher. Or you could use a Remote Desktop Connection to the access the virtual machine. Once connected, use test-connection. As you have time, give RDP a try.

Switch to the ManufacturingVM virtual machine.

In the Operations blade, select the Run command blade.

Select RunPowerShellScript and run the Test-NetConnection command. Be sure to use the private IP address of the CoreServicesVM.
<img width="881" height="423" alt="image" src="https://github.com/user-attachments/assets/cbed1c3f-05f5-444e-935b-fab4d522f73e" />

The test connection should succeed because peering has been configured. Your computer name and remote address in this graphic may be different.
<img width="886" height="618" alt="image" src="https://github.com/user-attachments/assets/b83a06f1-9ecd-41df-b2b2-a3c4341aaf11" />

**Task 6: Create a custom route**
In this task, you want to control network traffic between the perimeter subnet and the internal core services subnet. A virtual network appliance will be installed in the core services subnet and all traffic should be routed there.

Search for select the CoreServicesVnet.

Select Subnets and then + Subnet. Be sure to select Add to save your changes.
<img width="880" height="612" alt="image" src="https://github.com/user-attachments/assets/edc613af-9a52-4379-b207-692d2787941b" />

In the Azure portal, search for and select Route tables, select + Create.

Enter the following details, select Review + Create, and then select Create.
<img width="1099" height="508" alt="image" src="https://github.com/user-attachments/assets/4d17f0fd-a50f-4ae1-8605-4dc0c0e42639" />

After the route table deploys, Search for and select the Route Tables.

Select the resource (not the checkbox) rt-CoreServices

Expand Settings then select Routes and then Add. Create a route from a future Network Virtual Appliance (NVA) to the CoreServices virtual network.
<img width="610" height="603" alt="image" src="https://github.com/user-attachments/assets/b6820fce-eca0-492d-9ac1-c4e01cdcef52" />

Select + Add. The last thing to do is associate the route with the subnet.

Select Subnets and then + Associate. Complete the configuration.

<img width="604" height="613" alt="image" src="https://github.com/user-attachments/assets/a2628846-0dc7-424c-bce2-74f85e26103c" />


Note: I created a user defined route to direct traffic from the DMZ to the new NVA.



Key takeaways
Congratulations on completing the lab. Here are the main takeaways for this lab.

By default, resources in different virtual networks cannot communicate.
Virtual network peering enables you to seamlessly connect two or more virtual networks in Azure.
Peered virtual networks appear as one for connectivity purposes.
The traffic between virtual machines in peered virtual networks uses the Microsoft backbone infrastructure.
System defined routes are automatically created for each subnet in a virtual network. User-defined routes override or add to the default system routes.
Azure Network Watcher provides a suite of tools to monitor, diagnose, and view metrics and logs for Azure IaaS resources.
