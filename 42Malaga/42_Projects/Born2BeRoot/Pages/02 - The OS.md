## Operating System: 
**Selection**:
- Choose and install the latest stable version of Debian (recommended) or Rocky.
- Ensure SELinux (for Rocky) or AppArmor (for Debian) is running at startup and properly configured.

**System Setup:**
- Do not install any graphical interface (X.org or equivalent).
- Create at least 2 encrypted partitions using LVM.

### OS Choice
Selected Debian for it's popularity. Commonly used, plenty of documentation and support. Have previously used it for the Raspberry Pi. It uses common tools like `apt` for package mangment, and AppArmor.

AppArmor is a framework for enhancing security. It defines access rules for applications, deciding what files can be accessed and what rights can be given. It should be activated already since version 10. Check using `sudo aa-status`.





---
<<  [[01 - Virtual Box]] -|-[[03 - The Installation]]  >>

[[Walkthrough]]