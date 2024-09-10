![[Bonus-lsblk-output-example.png]]
Set up partitions correctly so you get a structure similar to the one above.

During installation at the `Partition Disks` section, select **manual**.
![[installation-partition-disks-manual.png]]
Then select the virtual hard disk
![[install-partition-hdd-select.png]]

Select the empty partition:
![[install-partition-select-empty.png]]

And create a new partition
![[install-partition-create-new.png]]

Begin by creating the first node in the example, sda1
![[install-partition-sda1.png]]
This partition will be 500M
![[install-partition-sda1-size.png]]
This is the partition for the OS and so this is our **primary** partition and create it at the beginning.
![[install-partition-primary.png]]

For this partition we need to set the mount point to `/boot`
![[install-partition-root-mount-point.png]]
![[install-partition-root-boot-mnt.png]]

Complete the partition setup.

Once we have completed the previous step, the partition appear. Now create a logical partition with all the available space on the disk, which has no mount point and is encrypted. To do this, we select the free space where we want to create it:
![[install-edit-partion.png]]
Now move on to sda5:
![[sda5.png]]

Create a new partition in this space:
![[Pasted image 20240910142432.png]]
![[sda5-max-space.png]]
\Make this a logical partition
![[install-logical-partition.png]]\
Modify the mount point and choose not to mount it:
![[Pasted image 20240910142656.png]]
This partition is going to be split further with these 'sub partitions' being mounted. 

Now configure encrypted volumes
![[Pasted image 20240910142752.png]]
Say yes to writing the scheme to disk
![[Pasted image 20240910142828.png]]

and create encrypted volumes:
![[Pasted image 20240910142850.png]]

Select the sda5 volume to encrypt:
![[Pasted image 20240910142925.png]]

![[Pasted image 20240910142943.png]]

![[Pasted image 20240910143006.png]]

![[Pasted image 20240910143025.png]]

![[Pasted image 20240910143037.png]]

![[Pasted image 20240910143056.png]]

 We will configure the logical volume manager.
 ![[Pasted image 20240910143145.png]]

![[Pasted image 20240910143205.png]]

We will create a new volume group. Volume groups group partitions
![[Pasted image 20240910143242.png]]

Enter the name we want to give it. `LVMGroup` as indicated in the subject.
![[Pasted image 20240910143331.png]]
Select the volume sda5
![[Pasted image 20240910143357.png]]

Create the remaining volumes:
![[Pasted image 20240910143440.png]]

Create a logical volume:
![[Pasted image 20240910143656.png]]
Select the volume group:
![[Pasted image 20240910143711.png]]
Enter the first logical volume name, `root`.
![[Pasted image 20240910143726.png]]
Enter the size as in the subject, 10G
![[Pasted image 20240910143748.png]]
Repeat for `swap`

![[Pasted image 20240910143842.png]]
![[Pasted image 20240910143905.png]]


home
```
	Size: 5GB
	Mount: /home
```
var
```
	Size: 3GB
	Mount: /var
```
srv
```
	Size: 3GB
	Mount: /srv
```
tmp
```
	Size: 3GB
	Mount: /tmp
```
var--log
```
	Size: 4GB
	Mount: /var/log
```

![[Pasted image 20240910144529.png]]

Now we need to configure the filesystem and mountpoints.
Select the home partition:
![[Pasted image 20240910144638.png]]

Chose Use As:
![[Pasted image 20240910144705.png]]
Pick Ext4
![[Pasted image 20240910144722.png]]

Modify the mount point:
![[Pasted image 20240910144748.png]]

![[Pasted image 20240910144800.png]]

![[Pasted image 20240910144816.png]]

Repeat:
Root:
![[Pasted image 20240910144850.png]]
Pick Ext4
![[Pasted image 20240910144722.png]]

![[Pasted image 20240910144925.png]]

![[Pasted image 20240910145000.png]]

![[Pasted image 20240910145017.png]]

srv:
Use Ext4 and set the mountpoint to /srv

Swap:
For swap instead of ext4, select `swap area`
![[Pasted image 20240910145158.png]]

tmp:
Use ext4 and mount to /tmp

var--log:
Use ext4 and mount to a manual location:
![[Pasted image 20240910145427.png]]

enter `/var/log`
![[Pasted image 20240910145453.png]]

Once the changes have been made, scroll to Finish partitioning...
![[Pasted image 20240910145542.png]]

Write the changes to disk:
![[Pasted image 20240910145607.png]]




![[finish_partitions.png]]


![[partitions.png]]



---
 <<  |  [[04 - Logging In & Setting Up]] >>