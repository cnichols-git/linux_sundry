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
## making a server 
  
#!/bin/bash

test=$(df -P /usr | awk '{print $5}')

notify-send -t 180000  $test
#echo $test
