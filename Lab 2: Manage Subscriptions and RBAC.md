# Lab Report: Role-Based Access Control (RBAC) in Azure

## Introduction
This lab focuses on **role-based access control (RBAC)** in Azure.  
I learned how to use **permissions** and **scopes** to control what actions identities can and cannot perform.

The lab was divided into four tasks:

1. Implement management groups  
2. Review and assign a built-in Azure role  
3. Create a custom RBAC role  
4. Monitor role assignments with the Activity Log  

---

## Task 1: Implement Management Groups
In this task, I created and configured management groups.  
Management groups are used to **logically organize and segment subscriptions**.  

They allow RBAC and Azure Policy assignments to be inherited by other management groups and subscriptions.  
For example, if an organization has a dedicated support team for Europe, all European subscriptions can be placed into a management group, granting support staff access to only those subscriptions.

### Steps:
1. Sign in to the [Azure portal](https://portal.azure.com) and search for **Microsoft Entra ID**.  
2. Under **Manage → Properties**, review **Access management for Azure resources**.  
   Ensure you can manage access to all Azure subscriptions and management groups in the tenant.  
   ![Access Management](https://github.com/user-attachments/assets/d09daf7c-2348-40de-bc5b-b1d8db9fb912)  
3. Search for and select **Management groups**.  
   On the blade, click **+ Create**.  
   Configure the group as shown:  
   ![Create Management Group](https://github.com/user-attachments/assets/ff37535c-7816-4da6-87ca-fb419915c9b6)  

**Note:** You may need to refresh the page for the new management group to appear.

---

## Task 2: Review and Assign a Built-in Azure Role
In this task, I reviewed built-in roles and assigned the **Virtual Machine Contributor** role to the IT Help Desk group.  
Azure provides many built-in roles; commonly used ones include **Owner**, **Contributor**, and **Reader**.

### Steps:
1. Select the **az104-mg154168746** management group.  
   Go to **Access control (IAM) → Roles tab**.  
   ![Roles Tab](https://github.com/user-attachments/assets/c7b9d47c-978b-4a8b-93cd-861af4f6ebc9)  
2. Scroll through the available role definitions and view details such as **Permissions, JSON, and Assignments**.  
   Example: viewing the **Owner** role.  
   ![Owner Role](https://github.com/user-attachments/assets/ef53c3c9-da41-4803-b1b5-7869f11f6f83)  
3. Click **+ Add → Add role assignment**.  
   From the blade, select **Virtual Machine Contributor**.  
   This role allows VM management but not access to the OS or virtual network/storage.  
   ![Add Role Assignment](https://github.com/user-attachments/assets/838483b1-23d3-4323-abfc-c19ace192577)  
4. On the **Members** tab, choose **Members → IT Helpdesk group → Select**.  
   ![Assign Role to IT Helpdesk](https://github.com/user-attachments/assets/e73f52b5-236a-4de6-bfcd-f6c1ba8e2754)  

Other tabs include **Conditions, Assignment type, and Review + Assign**.

---

## Task 3: Create a Custom RBAC Role
Built-in roles might have more permissions than needed.  
Custom roles help enforce the **principle of least privilege** by granting only the necessary permissions.

### Steps:
1. On the **Management group → Access control (IAM)** blade, select **+ Add → Add custom role**.  
2. Complete the **Basics tab** configuration:  
   ![Custom Role Basics](https://github.com/user-attachments/assets/93ce4aac-a253-4d30-9e02-cab8af4902b4)  
3. For **Baseline permissions**, select **Clone a role → Support Request Contributor**.  
   ![Clone Role](https://github.com/user-attachments/assets/8c2d47d9-fe4e-4677-bf80-34621639ba4d)  
4. On the **Permissions tab**, select **+ Exclude permissions**.  
   Search for `.Support` and choose **Microsoft.Support**.  
   ![Exclude Permissions](https://github.com/user-attachments/assets/0672af49-7253-412b-8d13-e33f20ced032)  
5. Review the **JSON** for Actions, NotActions, and AssignableScopes.  
   ![Custom Role JSON](https://github.com/user-attachments/assets/64e88bfa-afb8-4a99-8356-829cdc23cacf)  
6. Select **Review + Create → Create**.  
   ![Create Custom Role](https://github.com/user-attachments/assets/e7eceeeb-6250-4067-a4fa-2ce34c498eff)  

---

## Task 4: Monitor Role Assignments with the Activity Log
In this task, I viewed the **Activity Log** to monitor role assignment events.

1. Navigate to the **az104-mg154168746** resource.  
2. Select **Activity log** to review subscription-level events.  
3. Filter logs for **role assignment activities**.  

![Activity Log](https://github.com/user-attachments/assets/cd392edc-318d-4d8b-b804-aced4538bb52)  

---

## Conclusion
Through this lab, I gained hands-on experience with **RBAC in Azure**, including:  
- Organizing subscriptions with management groups  
- Assigning built-in roles  
- Creating custom roles with least privilege  
- Monitoring role changes with the Activity Log  

This knowledge is essential for securing Azure environments and enforcing access control effectively.
