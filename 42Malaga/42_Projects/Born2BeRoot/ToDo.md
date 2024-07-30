Select OS  - Why?
**Debian**  plenty of examples of it in use, lots of docs, used on all sorts of things including the RPi


- [ ] create at least 2 encrypted partitions using LVM
	- [ ] **Encryption Passphrase:** ==my stupid passphrase!==
- [ ] know the differences between aptitude and apt, or what SELinux or AppArmor is.
- [ ] it must not be possible to connect using SSH as root.
- [ ] Configure UFW (or firewalld for Rocky) firewall and leave only port 4242 open
- [x] The **hostname** of your virtual machine must be your **login ending with 42** (e.g., wil42).
- [ ] You will have to modify this hostname during your evaluation. 
- [ ] Implement a strong password policy:
	- [ ] Your password has to expire every 30 days.
	- [ ] The minimum number of days allowed before the modification of a password will be set to 2.
	- [ ] The user has to receive a warning message 7 days before their password expires.
	- [ ] Your password must be at least 
		- [ ] 10 characters long
		- [ ] uppercase letter
		- [ ] lowercase letter
		- [ ] and a number
		- [ ] It must not contain more than 3 consecutive identical characters.
		- [ ] ==**User:** sfarren **Pass:** 123ABCdef0==
	- [ ] The password **must not** include the name of the user.
	- [ ] *The following rule does not apply to the root password:* The password must have at least 7 characters that are not part of the former password. 
	- [ ] **the root password has to comply with this policy**
		- [ ] ==ROOT PASSWORD: 123ABCdef0 ~~RoOtP455word~~==
- [ ] You have to install and configure sudo following strict rules. 
	- [ ] Authentication using sudo has to be limited to 3 attempts in the event of an incorrect password. 
	- [ ] A custom message of your choice has to be displayed if an error due to a wrong password occurs when using sudo.
	- [ ] Each action using sudo has to be archived, both inputs and outputs. The log file has to be saved in the /var/log/sudo/ folder. The TTY mode has to be enabled for security reasons.
- [ ] For security reasons too, the paths that can be used by sudo must be restricted. Example: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin


- [ ] In addition to the root user, a user with your login as username has to be present.
- [ ] This user has to belong to the user42 and sudo groups.

- [ ] create a simple script called monitoring.sh. It must be developed in bash. 
- [ ] At server startup, the script will display some information on all terminals every 10 minutes (take a look at wall). 
- [ ] The banner is optional. 
- [ ] No error must be visible. 
- [ ] Your script must always be able to display the following information: 
	- [ ] The architecture of your operating system and its kernel version. 
	- [ ] The number of physical processors. 
	- [ ] The number of virtual processors. 
	- [ ] The current available RAM on your server and its utilization rate as a percentage. 
	- [ ] The current available storage on your server and its utilization rate as a percentage. 
	- [ ] The current utilization rate of your processors as a percentage. 
	- [ ] The date and time of the last reboot. 
	- [ ] Whether LVM is active or not. 
	- [ ] The number of active connections.
	- [ ] The number of users using the server.
	- [ ] The IPv4 address of your server and its MAC (Media Access Control) address.
	- [ ] The number of commands executed with the sudo program.
