VM Location:

OS Choice:

> [!NOTE]
> You must choose as an operating system either the latest stable version of Debian (no testing/unstable), or the latest stable version of Rocky. Debian is highly recommended if you are new to system administration. Setting up Rocky is quite complex. Therefore, you don’t have to set up KDump. However, SELinux must be running at startup and its configuration has to be adapted for the project’s needs. AppArmor for Debian must be running at startup too.

You must create at least 2 encrypted partitions using LVM. Below is an example of the expected partitioning


> [!NOTE]
> During the defense, you will be asked a few questions about the operating system you chose. For instance, you should know the differences between aptitude and apt, or what SELinux or AppArmor is. In short, understand what you use!

