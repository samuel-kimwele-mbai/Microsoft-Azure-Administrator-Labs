Lab introduction
In this lab you learn to create storage accounts for Azure blobs and Azure files. You learn to configure and secure blob containers. You also learn to use Storage Browser to configure and secure Azure file shares.
 This lab has three lab:

Task 1: Create and configure a storage account.
Task 2: Create and configure secure blob storage.
Task 3: Create and configure secure Azure file storage.


**Task 1: Create and configure a storage account.**
In this task, you will create and configure a storage account. The storage account will use geo-redundant storage and will not have public access.

Sign in to the Azure portal - https://portal.azure.com.

Search for and select Storage accounts, and then click + Create.

On the Basics tab of the Create a storage account blade, specify the following settings (leave others with their default values):
<img width="1090" height="427" alt="image" src="https://github.com/user-attachments/assets/b886cbf7-124b-4491-abbe-fe55c3fdff3f" />
<img width="1073" height="297" alt="image" src="https://github.com/user-attachments/assets/9166f03f-570e-4cf6-86b6-7d3134b7aa70" />

Did you know? You should use the Standard performance tier for most applications. Use the Premium performance tier for enterprise or high-performance applications.

On the Networking tab, in the Public network access section, select Disable. This will restrict inbound access while allowing outbound access.
<img width="1084" height="436" alt="image" src="https://github.com/user-attachments/assets/5838f7b6-fe59-4d28-9504-58ca37501f11" />

Review the Data protection tab. Notice 7 days is the default soft delete retention policy. Note you can enable versioning for blobs. Accept the defaults.
<img width="1094" height="361" alt="image" src="https://github.com/user-attachments/assets/01728424-d439-48a9-b8c9-04b9861cd300" />

Review the Encryption tab. Notice the additional security options. Accept the defaults.

<img width="1093" height="367" alt="image" src="https://github.com/user-attachments/assets/f94928f2-3998-4981-a923-bf12e4a3e975" />


Select Review + Create, wait for the validation process to complete, and then click Create.

Once the storage account is deployed, select Go to resource.

Review the Overview blade and the additional configurations that can be changed. These are global settings for the storage account. Notice the storage account can be used for
 Blob containers, File shares, Queues, and Tables.
 <img width="1091" height="604" alt="image" src="https://github.com/user-attachments/assets/66cedf76-b260-4e00-ab05-4d590c2b5c66" />
In the Security + networking blade, select Networking. Notice Public network access is disabled.

Select Manage and change the Public network access setting to Enabled.
Change the Public network access scope to Enable from selected networks.
In the IPv4 Addresses section, select Add your client IPv4 address.
Save your changes.
<img width="1094" height="494" alt="image" src="https://github.com/user-attachments/assets/41cd5c12-0d79-484f-8b98-2ec3f88655bb" />


In the Data management blade, select Redundancy. Notice the information about your primary and secondary data center locations.
<img width="1093" height="562" alt="image" src="https://github.com/user-attachments/assets/3c4d97e4-45fa-4712-872b-c60c693d0625" />

In the Data management blade, select Lifecycle management, and then select Add a rule.
<img width="1063" height="493" alt="image" src="https://github.com/user-attachments/assets/13c43481-1f0c-486a-a201-591b4eb63d03" />
<img width="1084" height="564" alt="image" src="https://github.com/user-attachments/assets/ea5cb1e8-8331-4620-b613-07808ae32bf5" />
Click add.

**Task 2: Create and configure secure blob storage**
In this task, you will create a blob container and upload an image. Blob containers are directory-like structures that store unstructured data.

Create a blob container and a time-based retention policy
Continue in the Azure portal, working with your storage account.

In the Data storage blade, select Containers.

Click + Add container and Create a container with the following settings:
<img width="1094" height="614" alt="image" src="https://github.com/user-attachments/assets/c8ca10c1-bf8e-4ad0-b7e2-a14c0c0356fc" />
the access has been set to private.

On your container, scroll to the ellipsis (…) on the far right, select Access Policy.

In the Immutable blob storage area, select Add policy.
<img width="1091" height="611" alt="image" src="https://github.com/user-attachments/assets/0c44228c-5a8a-418f-97ba-2aa754bfa9aa" />

Return to the containers page, select your data container and then click Upload.

On the Upload blob blade, expand the Advanced section.
<img width="1087" height="602" alt="image" src="https://github.com/user-attachments/assets/17b465b8-9baa-4b3d-8753-ed8f25be8183" />

<img width="1103" height="614" alt="image" src="https://github.com/user-attachments/assets/0f459dbc-a11c-400d-9514-0efdf4fd3f90" />

Click Upload.

Confirm you have a new folder, and your file was uploaded.
<img width="1089" height="607" alt="image" src="https://github.com/user-attachments/assets/4bf8c6e8-2441-494e-99f5-ad778a94ae78" />


Select your upload file and review the ellipsis (…) options including Download, Delete, Change tier, and Acquire lease.

Copy the file URL (Settings --> Properties blade) and paste into a new Inprivate browsing window.

You should be presented with an XML-formatted message stating ResourceNotFound or PublicAccessNotPermitted.

Note: This is expected, since the container you created has the public access level set to Private (no anonymous access).
<img width="1093" height="646" alt="image" src="https://github.com/user-attachments/assets/20145a3c-8b67-4b97-85fd-ff253b80c5fd" />

Configure limited access to the blob storage
Browse back to the file that you uploaded and select the ellipsis (…) to the far right, then select Generate SAS and specify the following settings (leave others with their default values):

<img width="1095" height="608" alt="image" src="https://github.com/user-attachments/assets/e0b58e36-d78c-4fc7-bac6-71656b1ec390" />

Click Generate SAS token and URL.

Copy the Blob SAS URL entry to the clipboard.

Open another InPrivate browser window and navigate to the Blob SAS URL you copied in the previous step.

Note: You should be able to view the content of the file. Mine was a downloadable file so here:
<img width="600" height="270" alt="image" src="https://github.com/user-attachments/assets/50753a7d-97d0-4415-bbe5-fc13bcfcd5fe" />

**Task 3: Create and configure an Azure File storage**
In this task, you will create and configure Azure File shares. You will use Storage Browser to manage the file share.

Create the file share and upload a file
In the Azure portal, navigate back to your storage account, in the Data storage blade, click File shares.
Click + File share and on the Basics tab give the file share a name, share1
<img width="1080" height="481" alt="image" src="https://github.com/user-attachments/assets/718ba9db-b88e-4ed0-b1ec-c21d18e613c6" />


Move to the Backup tab and ensure Enable backup is not checked. We are disabling backup to simplify the lab configuration.
<img width="1093" height="573" alt="image" src="https://github.com/user-attachments/assets/1666445c-866f-4819-8ee8-8ef8ec1d0dc0" />

Click Review + create, and then Create. Wait for the file share to deploy.


Explore Storage Browser and upload a file
Return to your storage account and select Storage browser. The Azure Storage Browser is a portal tool that lets you quickly view all the storage services under your account.

Select File shares and verify your share1 directory is present.
<img width="1083" height="600" alt="image" src="https://github.com/user-attachments/assets/4fa6f934-711c-4de3-ac1a-a83aad8b9375" />

Select your share1 directory and notice you can + Add directory. This lets you create a folder structure.

Select Upload. Browse to a file of your choice, and then click Upload.
<img width="1089" height="599" alt="image" src="https://github.com/user-attachments/assets/095e14b7-93b2-4c39-a878-1083b5732cb0" />
In the portal, search for and select Virtual networks.

Select + Create. Select your resource group. and give the virtual network a name, vnet1.

Take the defaults for other parameters, select Review + create, and then Create.
<img width="1092" height="603" alt="image" src="https://github.com/user-attachments/assets/aa9332f1-eaa7-487c-8836-00103b5c3944" />
Wait for the virtual network to deploy, and then select Go to resource.

In the Settings section, select the Service endpoints blade.
<img width="1092" height="612" alt="image" src="https://github.com/user-attachments/assets/9d33231d-6683-4dd8-a355-52f6d73af4f9" />

Return to your storage account.

In the Security + networking blade, select Networking.

Under Public network access select Manage.

Select Add a virtual network and then Add existing network.

Select vnet1 and default subnet, select Add.
<img width="1100" height="610" alt="image" src="https://github.com/user-attachments/assets/2d1d56c9-c8c2-4014-9dd8-d306a843066b" />
In the IPv4 Addresses section, Delete your machine IP address. Allowed traffic should only come from the virtual network.

Be sure to Save your changes.
<img width="1097" height="569" alt="image" src="https://github.com/user-attachments/assets/c59435e5-8383-4bb1-a63a-6cdd0e509fc5" />

Select the Storage browser and Refresh the page. Navigate to your file share or blob content.

Note: You should receive a message not authorized to perform this operation. You are not connecting from the virtual network. It may take a couple of minutes for this to take effect. 
You may still be able to view the file share, but not the files or blobs in the storage account.
<img width="1107" height="659" alt="image" src="https://github.com/user-attachments/assets/ee68ce3f-accd-4b97-98d4-38614d475c94" />


Key takeaways
Congratulations on completing the lab. Here are the main takeaways for this lab.

An Azure storage account contains all your Azure Storage data objects: blobs, files, queues, and tables. The storage account provides a unique namespace for your Azure Storage data that is accessible from anywhere in the world over HTTP or HTTPS.
Azure storage provides several redundancy models including Locally redundant storage (LRS), Zone-redundant storage (ZRS), and Geo-redundant storage (GRS).
Azure blob storage allows you to store large amounts of unstructured data on Microsoft's data storage platform. Blob stands for Binary Large Object, which includes objects such as images and multimedia files.
Azure file Storage provides shared storage for structured data. The data can be organized in folders.
Immutable storage provides the capability to store data in a write once, read many (WORM) state. Immutable storage policies can be time-based or legal-hold.
