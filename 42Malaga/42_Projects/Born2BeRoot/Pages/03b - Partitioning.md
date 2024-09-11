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
![[install-partition-create-new.png]]
![[sda5-max-space.png]]
\Make this a logical partition
![[install-logical-partition.png]]\
Modify the mount point and choose not to mount it:
![[install-partition-mount-location.png]]
This partition is going to be split further with these 'sub partitions' being mounted. 

### Encrypted Volumes
Now configure encrypted volumes
![[install-partitions-config-encrypted.png]]
Say yes to writing the scheme to disk
![[install-partitions-confirm-encrypt.png]]

and create encrypted volumes:
![[install-partitions-create-encrypt.png]]

Select the sda5 volume to encrypt:
![[install-partitions-select-encrypted-vol.png]]

![[install-partitions-finish-setting-encrypted-vol.png]]

![[install-partitions-finish-encryption.png]]

![[install-partitions-confirm-encryption.png]]

![[install-partitions-erase-disk.png]]

![[install-partitions-set-passphrase.png]]

 We will configure the logical volume manager.
 ![[install-partitions-config-lvm.png]]

![[install-partitions-write-lvm.png]]

We will create a new volume group. Volume groups group partitions
![[install-partitions-create-vol-group.png]]

Enter the name we want to give it. `LVMGroup` as indicated in the subject.
![[install-partitions-name-vol-group.png]]
Select the volume sda5
![[install-partitions-sda5-as-vol-group.png]]

Create the remaining volumes:
![[install-partitions-bonus-example-setup.png]]

Create a logical volume:
![[install-partitions-create-encrypted-volumes.png]]
Select the volume group:
![[install-partitions-select-vol-group.png]]
Enter the first logical volume name, `root`.
![[install-partitions-name-encrypted-volume.png]]
Enter the size as in the subject, 10G
![[install-partitions-set-vol-size.png]]
Repeat for `swap`

![[install-partitions-name-swap.png]]
![[install-partitions-set-swap-size.png]]


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

![[install-partitions-finish-creating-enc-vols.png]]

Now we need to configure the filesystem and mountpoints.
Select the home partition:
![[install-partitions-setting-mountpoints.png]]

Chose Use As:
![[install-partitions-set-filesytem.png]]
Pick Ext4
![[install-partitions-select-ext4.png]]

Modify the mount point:
![[install-partitions-set-home-mountpoint.png]]

![[install-partitions-home-mountpoint.png]]

![[install-partitions-done-home.png]]

Repeat:
Root:
![[Pasted image 20240910144850.png]]
Pick Ext4
![[install-partitions-select-ext4.png]]

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