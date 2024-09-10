For the project we will use VirtualBox, virtualisation software that creates a 'machine' that can run it's own operating system and applications separate from the host system. 

The VM provides a platform independent of their host system. This allows software developers and testers, for example, the opportunity to run their software in the same environment every time.  Their purpose is to provide a hardware platform and operating system independent execution environment, which hides the details of the underlying platform and allows a program to always run the same way on any platform.


Before the machine will run it will need an OS. This example uses Debian, https://www.debian.org/.
Download a copy of the ISO.

Open VirtualBox and create a new machine.

![[01-VirtualBoxManager.png]]
Follow the steps and fill out some settings such as RAM and Hard Drive size. 
For the RAM set something like `1024MB`
For the HDD, to try to replicate the setup for the bonus set about `30GB`

Select the ISO image (or download one now!) and finish the setup process. 

Once complete, press the start button.

Example using Debian


---
<<  [[Walkthrough]] -|- [[02 - The OS]]  >>
