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
