# linux_sundry  

## Adding a mounted device  
<pre>lvcreate -L 700G -n data rhel</pre>  
**Show the logical volumes  
<pre>lvdisplay</pre>  
Creat a file system on the device /dev/<volume group>  
<pre>mkfs.ext4 /dev/rhel/data</pre>
test the mounting
<pre># mount /dev/rhel/data /export/data</pre>
Modify the fstab so the device is mount at start up
```/dev/rhel/data                                        /export/data            ext4    defaults,x-systemd.device-timeout=0 1 2```
