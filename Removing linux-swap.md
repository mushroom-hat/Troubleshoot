# Problem
If you accidentally deleted linux-swap partition in gparted or similar disk management tool, this may cause your machine to boot up slower. If you often hibernate your machine, removing the swap file means that your machine will no longer be able to hibernate

## Error Messages
- No error messages, just longer & noticeable bootup times

# Solution
1) Create a new swap partition. You can do so by following this link https://askubuntu.com/questions/180730/how-do-i-restore-a-swap-partition-i-accidentally-deleted. 
2) Check the UUID of the new swap partition and copy the UUID (inside the quotation) of the swap partition, labeled TYPE="swap"
```zsh
$ sudo blkid
```
<br>

4) Edit ***/etc/fstab*** and replace the UUID of the swap partition to the one you just copied.

5) Do the same with ***/etc/initramfs-tools/conf.d/resume***, edit the UUID in the file. 

6) Update initramfs (this step comes after step 5 where you have edited the initrams resume file)
```zsh
$ update-initramfs -u
```

6) Reboot your machine, it should be boot up significantly faster now
