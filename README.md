# linux_sundry  

## Adding a mounted device  
We are creating a logical volume named "data" that is 700GB in the rhel volume group  
<pre>lvcreate -L 700G -n data rhel</pre>  
**Show the logical volumes**
Display all the logical volumes to show the newly created volume so we know the full path name
<pre>lvdisplay</pre>  
Creat a file system on the device /dev/<volume group>  
<pre>mkfs.ext4 /dev/rhel/data</pre>
Test the mounting
<pre># mount /dev/rhel/data /export/data</pre>
Modify the fstab so the device is mount at start up
<pre>/dev/rhel/data   /export/data    ext4    defaults,x-systemd.device-timeout=0 1 2</pre>  
## Not sure what I was doing here, but there ya go  
  
#!/bin/bash

test=$(df -P /usr | awk '{print $5}')

notify-send -t 180000  $test
#echo $test  
## Remove kernel from Linux install  
Went to the Boot menu and selected the other kernel listed. Machine boot up in cursed mode.  
opened a terminal.  
<pre>dpkg --list | grep -i -E --color 'linux-image|linux-kernel' | grep '^ii'</pre>  
found the Oracle image. on my computer it was listed as " linux-image-unsigned-5.19.0-1013-oracle 5.19.0-1013.14 amd64 Oracle Linux kernel image for  version 5.19.0 on 64 bit x86 SMP"  
Removed the "Oracle" image. sudo apt purge linux-image-5.19.0-1013-oracle  
sudo ubuntu-drivers install  
Rebooted.  
Sourcce : https://old.reddit.com/r/Ubuntu/comments/zb67sw/success_removed_oracle_image/  
