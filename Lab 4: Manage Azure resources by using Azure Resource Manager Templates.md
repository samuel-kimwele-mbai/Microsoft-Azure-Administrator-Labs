Lab introduction
In this lab, I learnt how to automate resource deployments. I learnt about Azure Resource Manager templates and Bicep templates. I learnt about the different ways of deploying the templates.

This lab has five tasks:

Task 1: Create an Azure Resource Manager template.
Task 2: Edit an Azure Resource Manager template and redeploy the template.
Task 3: Configure the Cloud Shell and deploy a template with Azure PowerShell.
Task 4: Deploy a template with the CLI.
Task 5: Deploy a resource by using Azure Bicep.

Task 1: Create an Azure Resource Manager template
In this task, I will create a managed disk in the Azure portal. Managed disks are storage designed to be used with virtual machines. Once the disk is deployed I will export a template 
that I can use in other deployments.

1. Sign in to the Azure portal - https://portal.azure.com. Search for and select Disks. On the Disks page, select Create.

2. On the Create a managed disk page, configure the disk and then select Ok.
<img width="661" height="610" alt="image" src="https://github.com/user-attachments/assets/652c0008-6c7f-41f7-93b3-5c9f46e70943" />

3. Click Review + Create then select Create. After the deployment, go to resource

4. In the Automation blade, select Export template. Click Download and save the templates to the local drive. This creates a compressed zipped file.
<img width="1438" height="784" alt="image" src="https://github.com/user-attachments/assets/3287d078-e51b-49f5-984d-92c1e2a727eb" />
5. Use File Explorer to extract the content of the downloaded file into the Downloads folder on your computer. Notice there are two JSON files (template and parameters).
Do you know? You can export an entire resource group or just specific resources within that resource group.

Task 2: Edit an Azure Resource Manager template and then redeploy the template
In this task, I used the downloaded template to deploy a new managed disk. This task outlines how to quicky and easily repeat deployments.

1. In the Azure portal, search for and select Deploy a custom template. On the Custom deployment blade, notice there is the ability to use a Quickstart template. There are many built-in templates as 
shown in the drop-down menu:
<img width="1188" height="720" alt="image" src="https://github.com/user-attachments/assets/598ea3bb-2d10-4043-aa69-d0b74da365cb" />

2. Instead of using a Quickstart, select Build your own template in the editor. On the Edit template blade, click Load file and upload the template.json file you downloaded to the local disk. Within the 
editor pane, make these changes.

Change disks_az104_disk1_name to disk_name (two places to change)
Change az104-disk1 to az104-disk2 (one place to change)

<img width="1426" height="736" alt="image" src="https://github.com/user-attachments/assets/e115fcdc-709f-4802-9611-0cafb457545c" />

click save

3. Now it is time to edit the parameters file. Select Edit parameters, click Load file and upload the parameters.json.

Make this change so it matches the template file.

**Change disks_az104_disk1_name to disk_name (one place to change)**

<img width="1452" height="384" alt="image" src="https://github.com/user-attachments/assets/61c79251-be7a-4741-b454-aeecff0a0341" />

4. Complete the custom deployment settings:
5. <img width="848" height="426" alt="image" src="https://github.com/user-attachments/assets/cb1b2532-a6c3-4d9b-8fb8-37334b2e15e3" />
6. Select Review + Create and then select Create and select Go to resource to verify az104-disk2 was created. On the Overview blade, select the resource group, az104-rg3. You should now have two disks.
<img width="1440" height="543" alt="image" src="https://github.com/user-attachments/assets/da5b294e-fad0-4bc1-bdb0-3fb984ed55cb" />

7. In the Settings section, click Deployments. Select a deployment and review the content of the Input and Template blades.
<img width="1409" height="234" alt="image" src="https://github.com/user-attachments/assets/fb1cea76-f313-4bab-87ca-414b7f6592d1" />
<img width="1429" height="288" alt="image" src="https://github.com/user-attachments/assets/42c80abc-28a2-4e36-9b47-d94dd6ec0939" />



Task 3: Configure the Cloud Shell and deploy a template with PowerShell
In this task, I worked with the Azure Cloud Shell and Azure PowerShell. Azure Cloud Shell is an interactive, authenticated, browser-accessible terminal for managing Azure resources. It provides the 
flexibility of choosing the shell experience that best suits the way you work, either Bash or PowerShell. In this task, you use PowerShell to deploy a template.

1. Select the Cloud Shell icon in the top right of the Azure Portal. Alternately, you can navigate directly to https://shell.azure.com
<img width="463" height="80" alt="image" src="https://github.com/user-attachments/assets/d45e45ab-f96a-400c-a478-c0e83d298067" />

2. When prompted to select either Bash or PowerShell, select PowerShell.

Note: If you mostly work with Linux systems, Bash (CLI) feels more familiar. If you mostly work with Windows systems, Azure PowerShell feels more familiar.

3. On the Getting started screen select Mount storage account, select your Storage account subscription, and then select Apply. Select I want to create a storage account and then Next. Complete the Create 
storage account information. When completed select Create.

<img width="814" height="275" alt="image" src="https://github.com/user-attachments/assets/82d6286c-fd22-4c9a-b62a-55abda38a904" />

4. Select Settings (top bar) and then Go to classic version. Select the Upload/Download files icon (top bar) and then select Upload. Upload both the template and parameters files from the Downloads directory.Select
 the Editor (curly brackets) icon and navigate to the template JSON file on the left in the navigation pane.

Make a change. For example, change the disk name to az104-disk3. Use Ctrl +S to save your changes. 
<<img width="1288" height="404" alt="image" src="https://github.com/user-attachments/assets/c63f49e2-28f9-454c-aeb1-f6d061dd0a22" />

5. To deploy to a resource group, use New-AzResourceGroupDeployment. Use the command: New-AzResourceGroupDeployment -ResourceGroupName az104-rg3 -TemplateFile template.json -TemplateParameterFile parameters.json

6. Ensure the command completes and the ProvisioningState is Succeeded.
<img width="1251" height="282" alt="image" src="https://github.com/user-attachments/assets/efa1e5a4-e355-4c80-87a9-7214c9456e1d" />

To confirm the disk was created use the command: Get-azDisk: <img width="980" height="714" alt="image" src="https://github.com/user-attachments/assets/792758fb-d79f-4cb7-9ad1-5fca693bc86d" />


Task 4: Deploy a template with the CLI

1. Continue in the Cloud Shell select Bash. Confirm your choice. Verify your files are available in the Cloud Shell storage Use the command **ls**. If you completed the previous task your template files 
should be available. <img width="327" height="132" alt="image" src="https://github.com/user-attachments/assets/3294e16d-7597-4b67-8786-f40315c8c29f" />

2. Select the Editor (curly brackets) icon and navigate to the template JSON file. Make a change. For example, change the disk name to az104-disk4. Use Ctrl +S to save your changes.
3. To deploy to a resource group, use az deployment group create. Use the command: az deployment group create --resource-group az104-rg3 --template-file template.json --parameters parameters.json
4. Confirm the disk was created by using the command:  az disk list --output table
   <img width="787" height="149" alt="image" src="https://github.com/user-attachments/assets/8e950c0b-450a-4f13-a795-171767d62362" />


Task 5: Deploy a resource by using Azure Bicep
In this task, I used a Bicep file to deploy a managed disk. Bicep is a declarative automation tool that is built on ARM templates.

1. Locate the F:\Allfiles\Labs\03\azuredeploydisk.bicep file. Continue working in the Cloud Shell in a Bash session. Select Manage files and then Upload the Bicep file to the Cloud Shell.

2. Click Editor and when prompted Confirm the switch to the Classic Cloud Shell. Select the azuredeploydisk.bicep file

Take a minute to read through the Bicep template file. Notice how the disk resource is defined.
<img width="636" height="661" alt="image" src="https://github.com/user-attachments/assets/eeccf54d-4c61-4be7-8227-bfc39e99ee53" />


3. Make the following changes:

Change the managedDiskName value, line 2, to az104-disk5.
Change the sku name value, line 26, to StandardSSD_LRS.
Change the diskSizeinGiB value; line 7, to 32.
Use Ctrl + S to save your changes.

4. Now, deploy the template using the command: az deployment group create --resource-group az104-rg3 --template-file azuredeploydisk.bicep
5. Confirm the disk was created using the command: az disk list --output table
<img width="723" height="146" alt="image" src="https://github.com/user-attachments/assets/4853f323-1e8a-471e-b7f4-f47b79f0fc8e" />


Key takeaways

- Azure Resource Manager templates let you deploy, manage, and monitor all the resources for your solution as a group, rather than handling these resources individually.
- An Azure Resource Manager template is a JavaScript Object Notation (JSON) file that lets you manage your infrastructure declaratively rather than with scripts.
- An Rather than passing parameters as inline values in your template, you can use a separate JSON file that contains the parameter values.
- Azure Resource Manager templates can be deployed in a variety of ways including the Azure portal, Azure PowerShell, and CLI.
- Bicep is an alternative to Azure Resource Manager templates. Bicep uses a declarative syntax to deploy Azure resources.
- Bicep provides concise syntax, reliable type safety, and support for code reuse. Bicep offers a first-class authoring experience for your infrastructure-as-code solutions in Azure.

