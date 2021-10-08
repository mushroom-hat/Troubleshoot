# Problem
When running Hashcat, there might be a clBuildProgram() error or device build fail. This likely has to do with your OpenCL backend device. The default hashcat (from kali) uses 'The POCL Project'. (verify this using Hashcat -I)



## Error Messages
- clBuildProgram(): CL_BUILD_PROGRAM_FAILURE
- error: unknown target CPU 'generic'
- Device #2: Kernel /usr/share/hashcat/OpenCL/shared.cl build failed.
<br>

![alt text](https://github.com/mushroom-hat/Troubleshoot/blob/main/Hashcat%20Build%20Error/Images/hashcat_error.png?raw=true)
# Solution
Download the opencl runtime in the current directory
```console
mushroomh4t@kali:~$ wget http://registrationcenter-download.intel.com/akdlm/irc_nas/12556/opencl_runtime_16.1.2_x64_rh_6.4.0.37.tgz
```
<br>

Unzip it using tar, this will create a bash script 'install.sh'
```console
mushroomh4t@kali:~$ tar zxvf opencl_runtime_16.1.2_x64_rh_6.4.0.37.tgz 
```
<br>

Run the bash script, this will cause a popup. Personally, I followed the default settings. 
```console
mushroomh4t@kali:~$ sudo bash opencl_runtime_16.1.2_x64_rh_6.4.0.37/install.sh
```
<br>

After installing, run hashcat with the -I flag, if the installation is successful, you should an OpenCL Platform with Intel(R) Corporation as the Vendor. 
```console
mushroomh4t@kali:~$ hashcat -I
```
<br>

Verify that hashcat is able to run now using the benchmark flag. Depending on the platform ID of the Intel(R) OpenCL, use the -d flag to use that backend device.
```console
mushroomh4t@kali:~$ hashcat -b -d 1 
```
