Lab introduction
In this lab, you learn how to configure and test a public Load Balancer and an Application Gateway.

This lab has these task:

Task 1: Use a template to provision an infrastructure.
Task 2: Configure an Azure Load Balancer.
Task 3: Configure an Azure Application Gateway.
Task 1: Use a template to provision an infrastructure
In this task, you will use a template to deploy one virtual network, one network security group, and three virtual machines.

Download select the F:\Allfiles\Labs\Lab06 lab files (template and parameters).

Sign in to the Azure portal - https://portal.azure.com.

Search for and select Deploy a custom template.

On the custom deployment page, select Build your own template in the editor.

On the edit template page, select Load file.

Locate and select select the F:\Allfiles\Labs\Lab06\az104-06-vms-template.json file and select Open.

Select Save.

Select Edit parameters and load select the F:\Allfiles\Labs\Lab06\az104-06-vms-parameters.json file.
<img width="1093" height="659" alt="image" src="https://github.com/user-attachments/assets/93e36290-a41a-4e95-824a-cfc2d3792412" />


Select Save.

Use the following information to complete the fields on the custom deployment page, leaving all other fields with the default value.

<img width="1082" height="574" alt="image" src="https://github.com/user-attachments/assets/63d6e730-d519-4c74-90ef-3c7ee1bd9822" />

<img width="1061" height="626" alt="image" src="https://github.com/user-attachments/assets/846a9d71-f498-4000-80c8-ed303f54b883" />


Task 2: Configure an Azure Load Balancer
In this task, you implement an Azure Load Balancer in front of the two Azure virtual machines in the virtual network. Load Balancers 
in Azure provide layer 4 connectivity across resources, such as virtual machines. Load Balancer configuration includes a front-end IP address 
to accept connections, a backend pool, and rules that define how connections should traverse the load balancer.



In the Azure portal, search for and select Load balancers and, on the Load balancers blade, click + Create.

Create a load balancer with the following settings (leave others with their default values) then click Next: Frontend IP configuration:

<img width="1081" height="559" alt="image" src="https://github.com/user-attachments/assets/98de49d0-ec96-4456-b572-b35de31db3bb" />

On the Frontend IP configuration tab, click Add a frontend IP configuration and use the following settings:
<img width="1101" height="524" alt="image" src="https://github.com/user-attachments/assets/66463c9b-d3ef-43e2-89aa-9fcee1839d44" />

Note: The Standard SKU provides a static IP address. Static IP addresses are assigned with the resource is created and released when the resource is deleted.

On the Backend pools tab, click Add a backend pool with the following settings (leave others with their default values). Click Add and then Save. Click Next: Inbound rules.
<img width="1087" height="612" alt="image" src="https://github.com/user-attachments/assets/b2f82e40-65d0-431d-815f-937181aa2b8a" />

Click Add to add a virtual machine
<img width="1104" height="605" alt="image" src="https://github.com/user-attachments/assets/40c58a88-b312-402d-8c17-1d9f53b54a6b" />

click Review + create. Ensure there are no validation errors, then click Create.

Wait for the load balancer to deploy then click Go to resource.


Add a rule to determine how incoming traffic is distributed

In the Settings blade, select Load balancing rules.

Select + Add. Add a load balancing rule with the following settings (leave others with their default values). As you configure the rule use the informational icons to 
learn about each setting. When finished click Save.
<img width="1087" height="466" alt="image" src="https://github.com/user-attachments/assets/75e4baa1-0809-4169-9eb8-85f741081319" />



Health probe	Create new:
<img width="757" height="424" alt="image" src="https://github.com/user-attachments/assets/20e46e5f-4865-40ba-a7de-8496ac94aff2" />

<img width="1090" height="604" alt="image" src="https://github.com/user-attachments/assets/17851bb3-d7a5-4af4-b980-43b0264499cc" />

Select Frontend IP configuration from the Load Balancer page. Copy the public IP address.

Open another browser tab and navigate to the IP address. Verify that the browser window displays the message Hello World from az104-06-vm0 or Hello World from az104-06-vm1.
<img width="1103" height="704" alt="image" src="https://github.com/user-attachments/assets/a2e91c02-c35f-4e20-aa22-e10750613055" />


**Task 3: Configure an Azure Application Gateway**
In this task, you implement an Azure Application Gateway in front of two Azure virtual machines. An Application Gateway provides layer 7 load balancing, Web Application Firewall (WAF), SSL termination, and 
end-to-end encryption to the resources defined in the backend pool. The Application Gateway routes images to one virtual machine and videos to the other virtual machine.

In the Azure portal, search and select Virtual networks.

On the Virtual networks blade, in the list of virtual networks, click az104-06-vnet1.

On the az104-06-vnet1 virtual network blade, in the Settings section, click Subnets, and then click + Subnet.

Add a subnet with the following settings (leave others with their default values).
<img width="1090" height="654" alt="image" src="https://github.com/user-attachments/assets/01bc626c-4a73-42db-9870-59634163cf35" />

Click Add

Note: This subnet will be used by the Azure Application Gateway. The Application Gateway requires a dedicated subnet of /27 or larger size.<img width="1093" height="436" alt="image" src="https://github.com/user-attachments/assets/76389a25-1225-4662-a338-49e989adf23b" />

In the Azure portal, search and select Application gateways and, on the Application Gateways blade, click + Create.

On the Basics tab, specify the following settings (leave others with their default values):
<img width="1105" height="330" alt="image" src="https://github.com/user-attachments/assets/700b984c-b9e4-49f6-bbee-e1c9f55a007d" />

<img width="1105" height="330" alt="image" src="https://github.com/user-attachments/assets/c536c15a-8704-466d-af84-a5c9c4af1973" />


Click Next: Frontends > and specify the following settings (leave others with their default values). When complete, click OK.

<img width="1103" height="590" alt="image" src="https://github.com/user-attachments/assets/8e1d3e22-3a77-4cdf-bce6-84f6d763b5f7" />
Note: The Application Gateway can have both a public and private IP address.

Click Next : Backends > and then Add a backend pool. Specify the following settings (leave others with their default values). When completed click Add.

<img width="1092" height="611" alt="image" src="https://github.com/user-attachments/assets/097bd8b4-74e3-4010-9e2f-420d35623643" />
Click Add a backend pool. This is the backend pool for images. Specify the following settings (leave others with their default values). When completed click Add.

<img width="1096" height="622" alt="image" src="https://github.com/user-attachments/assets/a6c1d0f6-3f14-4df8-a60a-0906fb8e15f6" />

Click Add a backend pool. This is the backend pool for video. Specify the following settings (leave others with their default values). When completed click Add.

<img width="1091" height="617" alt="image" src="https://github.com/user-attachments/assets/ca8c7462-547b-4004-879c-fc61a589eed7" />

Select Next : Configuration > and then Add a routing rule. Complete the information.
<img width="1091" height="612" alt="image" src="https://github.com/user-attachments/assets/0cf03d35-3cda-47a2-8cf4-a2ef369155d6" />

Move to the Backend targets tab. Select Add after completing the basic information.
<img width="1096" height="619" alt="image" src="https://github.com/user-attachments/assets/e4c7ff00-2820-44ad-bf7a-292261223080" />

In the Path-based routing section, select Add multiple targets to create a path-based rule. You will create two rules. Click Add after the first rule and then Add after the second rule.
Rule - routing to the images backend
<img width="889" height="355" alt="image" src="https://github.com/user-attachments/assets/39c61e01-a909-4a82-a50f-6bc0ad72b7ff" />

Rule - routing to the videos backend
<img width="888" height="615" alt="image" src="https://github.com/user-attachments/assets/0af62cce-df1c-4f12-a6d0-c1b23a14ed8f" />

Be sure to check your changes, then select Next : Tags >. No changes are needed.

Select Next : Review + create > and then click Create.

After the application gateway deploys, search for and select az104-appgw.

In the Application Gateway resource, in the Monitoring section, select Backend health.

Ensure both servers in the backend pool display Healthy.
<img width="1092" height="610" alt="image" src="https://github.com/user-attachments/assets/f6eb42ba-ac8f-4286-a66a-4e4c14d2c647" />

