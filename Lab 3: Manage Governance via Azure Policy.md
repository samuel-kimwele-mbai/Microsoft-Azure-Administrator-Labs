# Lab Report: Implementing Governance with Azure Policies, Tags, and Locks

## Introduction
In this lab, I learned how to implement governance plans for my organization using **Azure Policies**, **Tags**, and **Resource Locks**.  

Key learnings:  
- How Azure Policies enforce operational decisions across an organization  
- How tags improve reporting and resource organization  
- How locks prevent accidental modifications or deletions  

⚠️ **Note:** This lab requires an Azure subscription. The subscription type may affect feature availability. The steps were written using **East US** as the region, but another region may be used.  

The lab was divided into four tasks:  
1. Create and assign tags via the Azure portal  
2. Enforce tagging via an Azure Policy  
3. Apply tagging via an Azure Policy  
4. Configure and test resource locks  

---

## Task 1: Assign Tags via the Azure Portal
Tags are a critical part of an Azure governance strategy as defined by the **Microsoft Well-Architected Framework** and **Cloud Adoption Framework**.  
They allow you to label resources with key-value pairs such as **owner, cost center, or sunset date**.

### Steps:
1. Sign in to the [Azure portal](https://portal.azure.com).  
   Search for and select **Resource groups** → **+ Create**.  
2. Fill in the settings as shown:  
   ![Create Resource Group](https://github.com/user-attachments/assets/473a4cc0-c65b-44ff-af5e-44776db74fa9)  
3. On the **Tags tab**, provide information for a new tag.  
   Example: `Cost Center = 000`  
   ![Add Tag](https://github.com/user-attachments/assets/c9b0762b-e867-4516-87db-c3acbc264525)  
4. Review and create the resource group.  
   ![Review and Create](https://github.com/user-attachments/assets/1eaa5df5-e562-440e-bd4a-160c84ba1159)  

---

## Task 2: Enforce Tagging via an Azure Policy
In this task, I used the **Require a tag and its value on resources** built-in policy to enforce governance.  

Azure Policy can enforce configurations on subscriptions, resource groups, or individual resources.

### Steps:
1. In the Azure portal, search for **Policy → Definitions**.  
   Browse through built-in policy definitions.  
2. Search for **Require a tag and its value on resources**, review the definition, then **Assign Policy**.  
   ![Require a Tag Policy](https://github.com/user-attachments/assets/6e2b46bc-cd8d-4621-a23d-2bdd6e1a602e)  
3. Configure assignment basics:  
   ![Assignment Basics](https://github.com/user-attachments/assets/3b783b3c-7777-435c-ab75-e7f84bb00153)  
4. Set **Parameters**:  
   ![Policy Parameters](https://github.com/user-attachments/assets/7aafd305-b0ae-431f-8ed8-14eee4a9f421)  
   (Remediation tab example:)  
   ![Remediation](https://github.com/user-attachments/assets/02283a3c-5790-492b-9338-a6a25a58f533)  
5. Review + Create.  
6. Test the policy:  
   - Create a new **Storage Account** without adding the required tag.  
   ![Storage Account](https://github.com/user-attachments/assets/6cf02381-ab3f-492e-9e72-0f191fcf953c)  
   - Validation fails because the resource did not include the **Cost Center** tag.  
   ![Validation Failed](https://github.com/user-attachments/assets/4f5f7016-20d5-4486-9970-2a451a30e68a)  

---

## Task 3: Apply Tagging via an Azure Policy
In this task, I remediated non-compliant resources by applying a policy that **inherits tags** from the parent resource group.  

### Steps:
1. Delete the earlier assignment (**Require a tag and its value on resources**).  
   ![Delete Assignment](https://github.com/user-attachments/assets/36777574-408f-4c88-ab1f-9c3f63aef2c9)  
2. Assign a new policy: **Inherit a tag from the resource group if missing**.  
   ![Inherit Policy](https://github.com/user-attachments/assets/0559d30b-5143-46f6-972b-ac0acaf02230)  
3. Configure assignment basics:  
   ![Assignment Basics](https://github.com/user-attachments/assets/f619a008-3576-4ad0-af7f-13a3a2bb92dd)  
4. Set parameters:  
   ![Policy Parameters](https://github.com/user-attachments/assets/1003fbc5-bb61-4186-bbf5-aab32ae3e4f7)  
5. Configure remediation (requires a managed identity):  
   ![Remediation Settings](https://github.com/user-attachments/assets/a65073a1-edf-4879-b442-09ac54d3af20)  
6. Review + Create.  
7. Test the policy:  
   - Create a new **Storage Account** without a tag.  
   ![New Storage Account](https://github.com/user-attachments/assets/c26cae63-a8ab-4c25-8167-047ebda45504)  
   - Validation passes this time.  
   ![Validation Passed](https://github.com/user-attachments/assets/0df37256-42d2-47a5-a287-78ac8e5cfdd4)  
   - On the resource’s **Tags blade**, the **Cost Center = 000** tag was automatically inherited.  
   ![Inherited Tag](https://github.com/user-attachments/assets/17a86c90-7d8e-4c0d-9212-31b200d1a6bd)  

---

## Task 4: Configure and Test Resource Locks
Resource locks prevent accidental deletion or modification of Azure resources.  
Locks override user permissions.

### Steps:
1. Open the **Resource Group** → **Settings → Locks**.  
2. Add a new lock and configure details.  
   ![Add Lock](https://github.com/user-attachments/assets/a243fa5b-ae74-497f-a061-d12707fe6fba)  
3. Attempt to delete the locked resource group.  
   You will receive a **deletion denied notification**.  
   ![Delete Denied](https://github.com/user-attachments/assets/9c503390-b6ff-468f-bd1a-20577019c589)  

**Note:** To delete the resource group, you must first remove the lock.

---

## Key Takeaways
- **Azure Tags**: Key-value pairs that logically organize and describe resources.  
- **Azure Policy**: Enforces organizational standards and compliance.  
- **Remediation Tasks**: Bring resources into compliance with modify or deployIfNotExist definitions.  
- **Resource Locks**: Prevent accidental deletions or modifications.  
- **Security Positioning**:  
  - Policies = **pre-deployment** security  
  - RBAC & Locks = **post-deployment** security  

