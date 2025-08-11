# Lab 01 - Create Tenant & Manage Microsoft Entra ID Identities

## Part 1: Create a Tenant

1. **Login to the Azure Portal**  
   [https://portal.azure.com](https://portal.azure.com)

   ![Azure Portal](https://github.com/user-attachments/assets/497f6256-bd59-41a3-86d5-b6a1d33ff511)

2. **Search for Microsoft Entra**  
   - From the **Azure Active Directory Overview** blade, select **Manage Tenants**.
   - Click **+ Create** to create a new tenant.

3. **On the Basics tab** of the **Create a tenant** blade:  
   - Select **Microsoft Entra ID**  
   - Click **Next: Configuration**

4. **On the Configuration tab**, configure the following fields, then click **Review + Create** → **Create**:

   | Field                | Value                |
   |----------------------|----------------------|
   | Organization Name    | First AAD            |
   | Initial Domain Name  | firstaad53698430     |
   | Country/Region       | United States        |

   ![Tenant Configuration](https://github.com/user-attachments/assets/00508316-b88d-4412-8fa5-df1b9cb668ee)

5. **Verification**  
   - Complete the "I am not a robot" verification.

   ![Verification](https://github.com/user-attachments/assets/9303f87b-2c0d-4aa1-9226-d61a066ba846)

6. **Tenant Creation**  
   - Once successful, you’ll see a confirmation message.  
   - Click the link to navigate to your new tenant and select **First AAD**.

---

## Part 2: Manage Microsoft Entra ID Identities

Microsoft Entra ID uses **users** and **groups** as the core building blocks of an identity solution.

### Architecture Diagram
![Architecture Diagram](https://github.com/user-attachments/assets/abbcf3f4-4f28-4ff0-9f06-80020672a9b6)

---

## Tasks

### Task 1: Create and Configure User Accounts

1. **Sign in** to the [Azure portal](https://portal.azure.com).  
   - Select **Cancel** if prompted with the Welcome to Azure splash screen.
   
2. **Search for Microsoft Entra ID** (Azure's cloud-based identity and access management solution).

3. **Create a New User**  
   - Go to **Users** → **New User** → **Create new user**.  
   - Fill in details as shown:

     ![Create User](https://github.com/user-attachments/assets/4157d39c-c554-4692-80de-7af277ea2fda)

   **Notes:**
   - The **Properties** tab includes details like first/last name, user type (Member/Guest), authorization info, job title, company name, department, etc.
   - The **Assignments** tab allows assigning roles or adding the user to a group.

4. **Finalize Creation**  
   - Click **Review + Create** → **Create**.

   ![Review Create](https://github.com/user-attachments/assets/f427f899-ffa8-4f40-a51e-0c422c5d3774)

---

### Invite an External User

1. **From the New User dropdown**, select **Invite an external user**.  
   Fill in the **Basics** tab:

   | Setting             | Value                                 |
   |---------------------|---------------------------------------|
   | Email               | your email address                    |
   | Display name        | your name                             |
   | Send invite message | ✔                                     |
   | Message             | Welcome to Azure and our group project|

2. **Properties tab**:

   | Setting          | Value                  |
   |------------------|------------------------|
   | Job title        | IT Lab Administrator   |
   | Department       | IT                     |
   | Usage location   | United States          |

3. **Send Invite**  
   - Click **Review + Invite** → **Invite**.

4. **Verify User**  
   - Refresh and confirm the invited user appears.

   ![Invited User](https://github.com/user-attachments/assets/cbf45196-6f30-49b0-a84a-4d4abe5a78e0)

---

### Task 2: Create Groups and Add Members

Group accounts can include **users** or **devices**.  
Two membership types:
- **Static** – Members are manually added/removed by admins.
- **Dynamic** – Members update automatically based on account/device properties (requires Entra ID Premium P1/P2).

---

1. **In the Azure portal** → Search for **Microsoft Entra ID** → **Groups**.

   **Group Options:**
   - **Expiration**: Set a group lifetime in days (requires renewal after expiry).
   - **Naming Policy**: Block specific words, add prefixes/suffixes.

2. **Create a Group**  
   - Click **+ New Group** and fill in details:

     ![Create Group](https://github.com/user-attachments/assets/d31b9078-e326-4e7c-8062-31be91ab808d)

   - No owners selected; add members manually (selected myself).

---

## Key Takeaways

- A **tenant** represents your organization’s Microsoft cloud services environment for both internal and external users.
- **Microsoft Entra ID** supports **user** and **guest** accounts with different access levels.
- **Groups**:
  - Two types: **Security** and **Microsoft 365**.
  - Membership: **Static** or **Dynamic**.
