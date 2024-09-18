## Virtual Machines

A virtual machine (VM) is a software emulation of a physical computer, capable of executing programs like a physical machine. VMs allow multiple operating systems and applications to run simultaneously on the same host machine, allowing for resource allocation, isolation, and flexibility. 

They're used in various scenarios, such as testing software in different environments, creating secure sandboxes, and optimizing server utilization. Using the VM we can ensure that the environment is in the same/required state each time.
 

## Debian vs CentOS
 
 The basic differences between CentOS and Debian?  

Debian tends to have a longer release cycle and provides more frequent updates through its various branches.  Where as CentOS has a slower release cycle, but provides LTS for up to 10 years for each major version. CentOS tends to be known for its stability and so might be favoured for production servers. Whereas Debian provides a wide range of packages and is often more up-to-date.

In terms of support both OSes have a strong community, however CentOS having a more enterprise focus tends to lean towards 'professional' support options. Debian has a strong, large and active community that provides extensive support and documentation. Debians use in products such as the Raspberry Pi (and other SBCs) increased its visibility and accessibility and with this more docs and other resources. 

Other than this there are some software differneces such as Debina uses the Advanced Package Tool `(apt)` and CentOS uses Yellowdog Updater Modified (`yum`)/DNF.

Debian uses the newere `systemd` for system managment but CentOs was using/uses `sysvinit`. Newer versions of CentOS offer `systemd` as an alternative (apparently). 

### My Choice:
I selected Debian for its easy to access documentation and support channels. It is also an OS I have used previously in its RPi form and also with the Debian based Ubuntu.

It uses common tools like `apt` for package mangment, and AppArmor.

### Differences between apt and aptitude ↙️

Aptitude is an enhanced version of apt. APT is a lower-level package manager where as aptitude is seen as a high-level package manager because of its GUI. Another big difference is the functionality offered by both tools. Both are able to provide the necessary means to perform package management.
### APPArmor

AppArmor is a framework for enhancing security. It defines access rules for applications, deciding what files can be accessed and what rights can be given. 
*It should be activated already since version 10. Check using `sudo aa-status`.*

### What is LVM

It is a logical volume manager. It provides a method for allocating space on mass storage devices, which is more flexible than conventional partitioning schemes for storing volumes.


 
