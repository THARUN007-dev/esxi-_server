# esxi-_server
create a new esxi server


Download VMware in this website:


link: https://www.softpedia.com/get/System/OS-Enhancements/VMware-Workstation.shtml

images:
![](images/Vmaredownload.png)


Download the VMware esxi server:
--

link: https://archive.org/details/vmware-esxi-7!

-->CLICK ISO image

![](images/esxidownload.png)

-----------------------------------------------------------------------------------------------------------

Install Vmware Workstation pro and click create a new vm icon

step -1
![](images/vm1.png)

step -2
![](images/vm2.png)

step -3
![](images/vm3.png)

step -4
![](images/vm4.png)

step -5
![](images/vm5.png)

step -6
![](images/vm6.png)

------------------------------------------------------------------------------------------------------------
 Install Esxi server:

 ![](images/vm11.png)

 step-1
 \
 ![](images/vm12.png)  

 --> Click f2 .enter a username is default and enter the password
 
 ![](images/vm13.png)

 step -2

 --->click network configuration .and enter ,go to ipv4 netwotk.check it option 2 is selected

  ![](images/vm14.png)    ![](images/vm15.png)

  step -3

  ----> Save and go to main page and view the ip addr 

   ![](images/vm16.png)

-------------------------------------------------------------------------------------------------------------

Browser page:

Your procedure for creating and running a VM in ESXi is correct. Here is the clean step-by-step version.
Create and run a virtual machine in VMware ESXi
1. Open the ESXi Web Interface.
2. Enter your username and password (root).
3. Go to Virtual Machines → Create / Register VM.
4. Select Create a new virtual machine.
5. Enter the VM name (example: raj_vm).
6. Select Guest OS Family and Guest OS Version/Distribution.
7. Click Next.
8. Select a datastore.
9. Configure CPU, RAM, hard disk and network.
10. Click Finish.
11. Find your VM name in the left-side Virtual Machines menu.
12. Select the VM and click Power on.
13. Open the VM Console to run it.
Important: Your current error
Your VM is already created, but the console shows:

Expected system overhead exceeds amount of installed physical memory.

This is a memory allocation issue, not a VM creation issue.

step-1

 ![](images/vm21.png)

 step-2

  ![](images/vm22.png)

  step-3

   ![](images/vm23.png)   ![](images/vm24.png)

   ![](images/vm25.png)    ![](images/vm26.png)

  ![](images/vm27.png)      ![](images/vm28.png)

  ----------------------------------------------------------------------------------------------------------

  ERROR OCCURS:

  --> VTX on in vmware
  Intel VT-x Error in VMware Workstation – Problem and Solution
1. What is VT-x?
Intel VT-x (Intel Virtualization Technology) is a hardware feature in Intel processors that allows a computer to run multiple virtual machines efficiently.

2. Common VT-x error
You may encounter this error in VMware Workstation:
VMware Workstation does not support
nested virtualization on this host.

Module 'HV' power on failed.

Intel VT-x might be disabled if it has not
been enabled in BIOS/firmware.
---->CMD
    systeminfo
---its shows

Another possible Windows message:
A hypervisor has been detected.
Features required for Hyper-V will not be displayed.


3. Main reasons for the error
1. Intel VT-x is disabled in BIOS.
2. Windows Hyper-V is using virtualization.
3. Memory Integrity (VBS) is enabled.
4. VMware Workstation cannot access hardware virtualization.
5. Nested virtualization is not enabled for the virtual machine.
4. How to solve the VT-x error
Method 1: Enable Intel VT-x in BIOS
1. Restart your laptop.
2. Press F2 to enter BIOS.
3. Find Intel Virtualization Technology.
4. Change it to Enabled.
5. Save and restart.
Your BIOS virtualization is already enabled.
Method 2: Disable Windows Hyper-V
--->Open CMD as Administrator:
        bcdedit /set hypervisorlaunchtype off


---> Restart Windows.
Method 3: Disable Windows virtualization features
--->Press Win + R, enter:
      optionalfeatures


Disable these if enabled:
- Hyper-V
- Virtual Machine Platform
- Windows Hypervisor Platform
- Windows Sandbox
Restart Windows.

Note: This can affect Docker Desktop and WSL2.
Method 4: Enable nested virtualization in VMware Workstation
Since you are running ESXi inside VMware Workstation:
1. Shut down the ESXi virtual machine.
2. Open VMware Workstation.
3. Select ESXi VM → Settings.
4. Go to Processors.
5. Enable:
   
   Virtualize Intel VT-x/EPT or AMD-V/RVI
6. Save and restart ESXi.
7. Verify VT-x
Open Command Prompt:
     systeminfo
Also check Task Manager → Performance → CPU → Virtualization.

For your nested ESXi setup, the most important setting is Virtualize Intel VT-x/EPT in VMware Workstation.

You have already successfully installed ESXi and accessed its web interface. Your next task is to ensure nested virtualization is enabled and allocate sufficient RAM.

