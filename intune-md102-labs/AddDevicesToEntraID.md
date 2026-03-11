# Microsoft Entra ID (Azure AD) Lab Series

This repository documents my hands-on experience with Microsoft Entra ID identity management.

---

## Lab 1: Entra ID Device Join (Windows 10)

### Objective
To join a Windows 10 workstation to a cloud-based Entra ID tenant for centralized management.

### Implementation Steps

1. **Initiate Join:** Navigate to Settings > Accounts > Access work or school and select "Join this device to Microsoft Entra ID."
![Step 1](Win10Entrajoin1.PNG)

2. **Organization Confirmation:** Verified the tenant `AkashChetryLab914.onmicrosoft.com` and confirmed the Administrator user type.
![Step 2](Win10 Entra Join 2.PNG)

3. **Success Verification:** The device confirmed a successful connection.
![Step 3](Win10 Entra Join 3.PNG)

4. **Final Status:** The "Access work or school" page now shows the active connection to the Entra ID tenant.
![Step 4](Win10 Entra Join 4.PNG)

5. **CLI Validation:** Used command prompt to verify the device hostname.
![Step 5](Win10 Entra Join 5.PNG)

---

## Lab 2: Entra ID Device Registration (Windows 11)

### Objective
To register a personal Windows 11 device (BYOD) to the Entra ID tenant to access corporate resources without full device management.

### Implementation Steps

1. **Initiate Registration:** On a Windows 11 machine, navigate to Settings > Accounts > Access work or school and clicked "Connect."
![Step 1](Win11Entraregistered1.PNG)

2. **Account Selection:** Navigated to the account settings to add the work or school credentials.
![Step 2](Win11Entraregistered2.PNG)

3. **Authentication:** Entered lab credentials for `akashchetry@akashchetrylab914.onmicrosoft.com` to begin the registration process.
![Step 3](Win11registered3.PNG)

4. **Confirmation:** Received confirmation that the account was successfully added to the device.
![Step 4](Win11registered4.PNG)

5. **Registration Success:** Final confirmation showing the device is now registered under the organization.
![Step 5](Win11registered5.PNG)

6. **CLI & Status Verification:** Verified the successful registration in the "Access work or school" menu and checked the local hostname via Command Prompt.
![Step 6](Win11registered6.PNG)

---
*Created by Akash Chetry*
