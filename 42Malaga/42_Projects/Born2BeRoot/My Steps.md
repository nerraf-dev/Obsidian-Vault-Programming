1. Open Virtualbox
2. Create a new VM
3. Fill in the details...mem (1GB, etc)
4. INSTALL
5. Set the hostname, new user, passwords, etc
6. Login as both users
7. SUDO as regular user - ERROR
8. Install sudo
	1. To install sudo, issue the command: `apt install sudo`
9. **Adding users to sudo**
	1. As `root` enter `usermod -aG sudo USERNAME`


- Configure SUDO
	- https://annvix.com/using_sudo_to_limit_access
- Make sure there are at least 2 encrypted partitions
- Add user42 group
- Add test user(s)
- Install UFW
- Block all ports except 4242 (used for SSH)



## [Configuring sudo](https://annvix.com/using_sudo_to_limit_access)
Sudo is easy to configure and uses a straightforward syntax. You use the command `visudo` to edit the file `/etc/sudoers`. `visudo` is a wrapper around your favorite editor that does syntax checking on the file when you are finished editing it. By default, if you don’t have the EDITOR variable set, visudo will use the vi editor. Arguments of editors aside, it is easy to change the editor that visudo calls.

You have to install and ==**configure** sudo== following strict rules. 
	- [ ] Authentication using sudo has to be limited to 3 attempts in the event of an incorrect password. 
	- [ ] A custom message of your choice has to be displayed if an error due to a wrong password occurs when using sudo.
	- [ ] Each action using sudo has to be archived, both inputs and outputs. The log file has to be saved in the /var/log/sudo/ folder. The TTY mode has to be enabled for security reasons.
- [ ] For security reasons too, the paths that can be used by sudo must be restricted. Example: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin