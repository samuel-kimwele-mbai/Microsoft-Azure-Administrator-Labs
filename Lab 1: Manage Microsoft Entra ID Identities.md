Create Tenant

1. Login to the Azure Portal https://portal.azure.com


<img width="1284" height="694" alt="image" src="https://github.com/user-attachments/assets/497f6256-bd59-41a3-86d5-b6a1d33ff511" />

2. Search for and select Microsoft Entra. From the Azure Active Directory Overview blade, select Manage Tenants and then select + Create to Create a new tenant.
3. On the Basics tab of the Create a tenant blade, select Microsoft Entra ID, then select Next: Configuration.

4. On the Configuration tab, configure the following fields then select Review + Create, and then Create:

Organization Name	First AAD
Initial Domain Name	firstaad53698430
Country/Region	United States

<img width="1287" height="660" alt="image" src="https://github.com/user-attachments/assets/00508316-b88d-4412-8fa5-df1b9cb668ee" />

You'll be required to verify that you are not a robot



<img width="539" height="307" alt="image" src="https://github.com/user-attachments/assets/9303f87b-2c0d-4aa1-9226-d61a066ba846" />

5. When the Tenant has been created, you will see text indicating Tenant creation was successful. Click here to navigate to your new tenant. Select the First AAD link.

Lab 01 - Manage Microsoft Entra ID Identities
This lab is about users and groups. Users and groups are the basic building blocks for an identity solution.
Architecture diagram
<img width="1028" height="534" alt="image" src="https://github.com/user-attachments/assets/abbcf3f4-4f28-4ff0-9f06-80020672a9b6" />

There are two tasks here: 
Task 1: Create and configure user accounts.
Task 2: Create groups and add members.

Task 1: Create and configure user accounts.
1. Sign in to the Azure portal - https://portal.azure.com. To proceed to the portal, select Cancel on the Welcome to Azure splash screen.
2. Search for and select Microsoft Entra ID. Microsoft Entra ID is Azure's cloud-based identity and access management solution.
3. Select Users, then in the New user drop-down select Create new user with settings as shown below:

<img width="1285" height="657" alt="image" src="https://github.com/user-attachments/assets/4157d39c-c554-4692-80de-7af277ea2fda" />

In the properties tab, you can have diffrent information about the user, this includes The user's: First and last name, user type(Member or Guest) authorization information and the second part, you had the job information related to the user which includes Job title, company name, department, etc
- Also, you have the asssignments tab where you can assign roles or add the user to a group.


4. select Review + create and then Create.
<img width="1294" height="657" alt="image" src="https://github.com/user-attachments/assets/f427f899-ffa8-4f40-a51e-0c422c5d3774" />

Invite an external user
1. In the New user drop-down select Invite an external user and fill the basics tab with this information: Setting	Value
Email	your email address
Display name	your name
Send invite message	check the box
Message	Welcome to Azure and our group project

2. Move to the Properties tab. Complete the basic information, including these fields.

Setting	Value
Job title	IT Lab Administrator
Department	IT
Usage location (Properties tab)	United States


3. Select Review + invite, and then Invite.


Refresh the page and confirm the invited user was created.
<img width="378" height="85" alt="image" src="https://github.com/user-attachments/assets/cbf45196-6f30-49b0-a84a-4d4abe5a78e0" />


Task 2: Create groups and add members
Here I created a group account. Group accounts can include user accounts or devices. These are two basic ways members are assigned to groups: Statically and Dynamically. Static groups require administrators to add and remove members manually. Dynamic groups update automatically based on the properties of a user account or device.

1. In the Azure portal, search for and select Microsoft Entra ID. In the Manage blade, select Groups.

Expiration lets you configure a group lifetime in days. After that time the group must be renewed by the owner.
Naming policy lets you configure blocked words and add a prefix or suffix to group names.

2. In the All groups blade, select + New group and create a new group and fill the fields as shown below:

<img width="1291" height="660" alt="image" src="https://github.com/user-attachments/assets/d31b9078-e326-4e7c-8062-31be91ab808d" />

no owners selected. Add members, here I selected myself.

Note: An Entra ID Premium P1 or P2 license is required for dynamic membership. If other Membership types are available, the options will show up in the drop-down.


The key takeaways from this lab:
- A tenant represents your organization and helps you to manage a specific instance of Microsoft cloud services for your internal and external users.
- Microsoft Entra ID has user and guest accounts. Each account has a level of access specific to the scope of work expected to be done.
- Groups combine together related users or devices. There are two types of groups including Security and Microsoft 365.
- Group membership can be statically or dynamically assigned.

