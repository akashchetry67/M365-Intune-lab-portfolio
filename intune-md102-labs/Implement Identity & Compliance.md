Lab 5: Intune Compliance Policies & Troubleshooting

1. Creating the Policy:
I created a policy named "North East Windows Compliance" for the Windows 10/11 platform.
()

2. Security Settings:
I required the Windows Firewall, Antivirus, and Antispyware to be active for a device to be considered healthy.
(Paste Compliance 6.png here)

3. Group Assignment:
The policy was assigned to my "North East Group" for automatic deployment.
(Paste Compliance 8.png here)

4. Monitoring and Results:
After deployment, I monitored the status. One device was marked as Noncompliant.
(Paste Compliance 11.png here)

5. Root Cause Analysis:
I drilled down into the device details and found the failure was caused by the Firewall being turned off.
