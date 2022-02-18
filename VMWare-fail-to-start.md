## About This Issue
When you update Windows 10 to Windows 11 while running VMWare version 16.2.1, you will find that you will be unable to start virtual machines that you have been using.

## Errors
An example errors that could occur in VMWare are:
- "vmware failed to start the virtual machine".
- "Exception 0xc0000005 (access violation) has occurred."


## Solution
1) Open CMD as Administrator
2) ```bcdedit /set hypervisorlaunchtype off```
3) Turn off "Windows Hypervisor Platform" if enabled in Windows Features
4) Reboot


More about this issue here https://communities.vmware.com/t5/VMware-Workstation-Pro/Workstation-16-1-2-Pro-under-Windows-11-host-Windows-guest-in-VM/m-p/2870506

