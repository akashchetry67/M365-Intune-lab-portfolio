# Intune Lab 1: Windows Device Enrollment

Objective

Enroll a Windows device into Microsoft Intune using Azure AD Join.

Environment

Tenant: Microsoft 365 E3  
Service: Microsoft Intune  
Device: Windows 11 VM

Steps

1. Open Settings
2. Go to Accounts
3. Select Access Work or School
4. Click Connect
5. Sign in with Microsoft 365 account

Verification

Open Intune Admin Center

Devices → Windows

Expected Result

The device appears as Managed.

Troubleshooting

Run command:

dsregcmd /status

Check AzureAdJoined status.

Interview Scenario

User device is not showing in Intune.

Steps to troubleshoot

Check Azure AD join  
Verify MDM auto enrollment  
Confirm license assignment
