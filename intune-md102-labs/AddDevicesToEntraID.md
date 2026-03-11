# Microsoft Entra ID (Azure AD) Lab Series

This repository documents my hands-on experience with Microsoft Entra ID identity management.

---

## Lab 1: Entra ID Device Join (Windows 10)

### Objective
To join a Windows 10 workstation to a cloud-based Entra ID tenant for centralized management.

### Implementation Steps

1. **Initiate Join:** Navigate to Settings > Accounts > Access work or school and select "Join this device to Microsoft Entra ID."
<img width="672" height="641" alt="Win10Entrajoin1" src="https://github.com/user-attachments/assets/27890371-e423-44b3-bf7a-c8691057debd" />


2. **Organization Confirmation:** Verified the tenant `AkashChetryLab914.onmicrosoft.com` and confirmed the Administrator user type.
<img width="1201" height="935" alt="Win10 Entra Join 2" src="https://github.com/user-attachments/assets/a71762ff-9906-433b-8c8a-d2b4858caa2b" />


3. **Success Verification:** The device confirmed a successful connection.
<img width="1210" height="938" alt="Win10 Entra Join 3" src="https://github.com/user-attachments/assets/458b939b-ae9e-4333-a533-0a0cc515fd8b" />


4. **Final Status:** The "Access work or school" page now shows the active connection to the Entra ID tenant.
<img width="1222" height="940" alt="Win10 Entra Join 4" src="https://github.com/user-attachments/assets/ed1c80bf-f9d7-4c4f-8322-d31b24901a5c" />


5. **CLI Validation:** Used command prompt to verify the device hostname.
<img width="1211" height="654" alt="Win10 Entra Join 5" src="https://github.com/user-attachments/assets/e1047bbb-f239-44fa-89f7-d42d1767b751" />


---

## Lab 2: Entra ID Device Registration (Windows 11)

### Objective
To register a personal Windows 11 device (BYOD) to the Entra ID tenant to access corporate resources without full device management.

### Implementation Steps

1. **Initiate Registration:** On a Windows 11 machine, navigate to Settings > Accounts > Access work or school and clicked "Connect."
<img width="1017" height="755" alt="Win11Entraregistered1" src="https://github.com/user-attachments/assets/cb79d47b-2c72-4b6c-ba1d-4446472dbb8d" />


2. **Account Selection:** Navigated to the account settings to add the work or school credentials.
<img width="999" height="751" alt="Win11Entraregistered2" src="https://github.com/user-attachments/assets/9e53c341-ae9e-4076-8e2f-3dc1e0474c99" />


3. **Authentication:** Entered lab credentials for `akashchetry@akashchetrylab914.onmicrosoft.com` to begin the registration process.
<img width="640" height="628" alt="Win11registered3" src="https://github.com/user-attachments/assets/eb5ada1e-a382-46de-beee-20c812c8e3eb" />


4. **Confirmation:** Received confirmation that the account was successfully added to the device.
<img width="664" height="643" alt="Win11registered4" src="https://github.com/user-attachments/assets/8a33b3fb-70ad-437c-b465-780a89fa01d7" />


5. **Registration Success:** Final confirmation showing the device is now registered under the organization.
<img width="665" height="640" alt="Win11registered5" src="https://github.com/user-attachments/assets/b6a3b7ae-5dcc-425c-9baf-857baaeb9da9" />


6. **CLI & Status Verification:** Verified the successful registration in the "Access work or school" menu and checked the local hostname via Command Prompt.
<img width="1031" height="746" alt="Win11registered6" src="https://github.com/user-attachments/assets/6a9ce90d-e48a-4a81-8231-7cab39892848" />


## Lab 3: Verification in Microsoft Entra Admin Center

### Objective
To verify that the devices from Lab 1 and Lab 2 have successfully synchronized with the cloud directory and to differentiate their join types within the Admin Portal.

### Implementation Steps

1. **Accessing the Portal:** Logged into the [Microsoft Entra admin center](https://entra.microsoft.com/) using Administrator credentials.
2. **Device Inventory:** Navigated to **Identity > Devices > All devices**.
3. **Data Validation:** * **DESKTOP-PM4PCDO:** Successfully verified as **Microsoft Entra joined** (Windows 10).
    * **Windows11:** Successfully verified as **Microsoft Entra registered** (Windows 11).
<img width="1918" height="927" alt="Screenshot 2026-03-11 202613" src="https://github.com/user-attachments/assets/633cfd65-17c0-40d5-842f-e103d80b3620" />

### **💡 Technical Note: Local Verification**

While the Entra Admin Center provides a high-level view, we can perform a deep-dive verification directly on the user's machine using the Command Line Interface (CLI). This is the primary method used for troubleshooting connectivity and synchronization issues.

**Command:**
`dsregcmd /status`

**Key Indicators to Look For:**
* **For Entra Joined:** Under the **Device State** section, verify that `AzureAdJoined : YES`.
* **For Entra Registered:** Under the **User State** section, verify that `WorkplaceJoined : YES`.

<img width="894" height="605" alt="Screenshot 2026-03-11 213517" src="https://github.com/user-attachments/assets/8f5fb788-5b8b-4c80-a0c3-c180e9a80b59" />


### Summary of Results
The Entra ID portal correctly reflects the state of both devices. This level of visibility allows IT Administrators to manage security compliance, BitLocker keys, and MDM enrollment from a single dashboard.

## Lab 4: Plan and Implement Groups in Microsoft Entra ID

### Objective
To organize devices into logical security groups using both **Assigned (Static)** and **Dynamic** membership types to facilitate scalable management in Microsoft Intune.

### Implementation Steps

1. **Accessing Group Management:** Navigated to the Groups section in the Microsoft Entra admin center to view existing M365 and Security groups.
![All Groups Overview] <img width="1880" height="888" alt="Group1" src="https://github.com/user-attachments/assets/11ec7357-a96d-46b5-8a07-956b7cd2c041" />


2. **Creating a New Security Group:** Initiated the creation of a new group titled "Windows Device Group."
![New Group Initiation] <img width="1181" height="873" alt="Group2" src="https://github.com/user-attachments/assets/1bc1e4c2-1307-4dd7-8dd8-727462343473" />


3. **Defining Membership Type:** * First, I explored **Assigned** membership for manual device addition.
   * Then, I selected **Dynamic Device** to implement automation rules.
![Membership Selection] <img width="1185" height="898" alt="Group3" src="https://github.com/user-attachments/assets/d789df91-5869-47ff-8267-263c461c9144" />


4. **Configuring Dynamic Rules:** I implemented a dynamic membership rule to automatically include devices based on their Operating System type.
   * **Rule Syntax:** `(device.deviceOSType -eq "Windows")`
![Dynamic Rule Syntax]<img width="1510" height="433" alt="Group5" src="https://github.com/user-attachments/assets/1020e884-51ab-4d82-b843-66ade3d29069" />
)

5. **Finalizing Group Creation:** Verified the group settings, including the description "All Windows Devices are included on this Group."
![Group Confirmation](<img width="1183" height="827" alt="Group4" src="https://github.com/user-attachments/assets/c48ff4e8-c8ba-4894-a0c9-8d70040740bc" />


6. **Verification of Membership:** Confirmed that the "Windows Device Group" successfully populated with the lab devices (`DESKTOP-PM4PCDO` and `Windows11`).
![Group Members Verification] <img width="1062" height="513" alt="Group6" src="https://github.com/user-attachments/assets/c7d7f107-f123-4911-92a2-c413c1fdf9ca" />


---

### **Key Takeaways**
* **Automation:** Dynamic groups eliminate the need for manual updates as new devices are onboarded.
* **Scalability:** By grouping by `deviceOSType`, I can ensure all Windows machines receive the same security baseline automatically.
* **Security:** Using Security groups instead of M365 groups ensures the group is optimized for Intune policy deployment.

---
*Created by Akash Chetry*
---
*Created by Akash Chetry*
