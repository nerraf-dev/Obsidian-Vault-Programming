## Operating System: 
**Selection**:
- Choose and install the latest stable version of Debian (recommended) or Rocky.
- Ensure SELinux (for Rocky) or AppArmor (for Debian) is running at startup and properly configured.

**System Setup:**
- Do not install any graphical interface (X.org or equivalent).
- Create at least 2 encrypted partitions using LVM.

### OS Choice
Selected Debian for it's popularity. Commonly used, plenty of documentation and support. Have previously used it for the Raspberry Pi. It uses common tools like `apt` for package mangment, and AppArmor.

### Differences between apt and aptitude ↙️

Aptitude is an enhanced version of apt. APT is a lower-level package manager where as aptitude is seen as a high-level package manager because of its GUI. Another big difference is the functionality offered by both tools. Both are able to provide the necessary means to perform package management.
### APPArmor

AppArmor is a framework for enhancing security. It defines access rules for applications, deciding what files can be accessed and what rights can be given. 
*It should be activated already since version 10. Check using `sudo aa-status`.*

### What is LVM

It is a logical volume manager. It provides a method for allocating space on mass storage devices, which is more flexible than conventional partitioning schemes for storing volumes.



---
<<  [[01 - The Virtual Machine]] -|-[[03a - The Installation]]  >>

[[Walkthrough]]
