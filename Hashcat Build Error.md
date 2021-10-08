# Problem
When running Hashcat, there might be a clBuildProgram() error or device build fail. This likely has to do with your OpenCL backend device. The default hashcat (from kali) uses The POCL Project. 
]

# Solution
```console
mushroomh4t@kali:~$ wget http://registrationcenter-download.intel.com/akdlm/irc_nas/12556/opencl_runtime_16.1.2_x64_rh_6.4.0.37.tgz

mushroomh4t@kali:~$ tar zxvf opencl_runtime_16.1.2_x64_rh_6.4.0.37.tgz 

mushroomh4t@kali:~$ cd opencl_runtime_16.1.2_x64_rh_6.4.0.37/

mushroomh4t@kali:~$ sudo bash install.sh
```
