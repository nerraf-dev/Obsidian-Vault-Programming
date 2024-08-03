Create a new VM in VirtualBox
![[01-VirtualBoxManager.png]]
RAM: 1024MB
HDD: 12GB

Example using Debian

## Operating System: 
**Selection**:
- Choose and install the latest stable version of Debian (recommended) or Rocky.
- Ensure SELinux (for Rocky) or AppArmor (for Debian) is running at startup and properly configured.

**System Setup:**
- Do not install any graphical interface (X.org or equivalent).
- Create at least 2 encrypted partitions using LVM.

Start the VM and follow the process.
"Do not install any graphical interface (X.org or equivalent)" So use the **Install** option
![[02-Installer.png]]
Go through localisation options.

> [!NOTE]
> **Hostname Configuration**: Set the hostname to your login ending with 42 (e.g., wil42).

The installer provides an option to set the hostname. It can be checked and edited again later via the [[hosts file]] method. 
![[03-Installer-Hostname.png]]

Set the `root` password

> [!NOTE]
> **Password Policy**:
>    - Passwords expire every 30 days.
>    - Minimum 2 days before a password can be modified.
>    - Warning 7 days before password expiration.
>    - Password must be at least 10 characters long, include uppercase, lowercase, and a number, and not have more than 3 consecutive identical characters.
>    - Root password must comply with the same policy except it must have at least 7 characters not part of the former password.

Root Password: 123ABCdef0



> [!NOTE] User Management
> Create a user with your login at the username belonging to user42 and sudo groups
> Be prepared to create a new user and assign it to a group during the defence.

The installer will create a non-admin user. This means that the user management part can be started.

![[04-Installer-NewUser.png]]

Set the user name and password as per the requirements.

User: sfarren
Pass: 123ABCdef0

   - Create at least 2 encrypted partitions using LVM.
Pick Use entire disk and set up encrypted LVM
![[05-Installer-LVM.png]]

Selecting this option creates 3 partions on the LVM encrypted volume
![[06-Installer-Partitions.png]]

The drive requires an encryption passphrase, enter this during install.

Passphrase: my stupid passphrase!

Allow the max size for partitioning and follow along.

The installer shows how the drive will be setup:
![[07-Drive setup.png]]
It shows two drives, with one of them being encrypted. 
![[08-partitions.png]]


The installer continues. When presented with a choice of install options turn it all off. There is no need for x.org or other GUI content. 

The installer can setup SSH, but in this attempt I will go through installing it myself with `apt`. Other tools need installing such as `sudo` and `ufw`.

Once installation is complete, login as `root` and standard users to test. 
From the user management section, a user has to be created and added to the `sudo` group (as well as `user42`). 

`sudo` needs to be installed using `apt` as the `root` user.
Switch the root user using `su -`. The - allows access to commands such as `usermod` located in a specific location.  Run `apt update && apt upgrade`. Then install `sudo` 

Once installed, as `root` enter `usermod -aG sudo USERNAME` with USERNAME being whoever you want to add to the group.

exit from root, and logout. Log back in as the standard user to test sudo.

Create a new group `user42` and add the existing user and new user to it. 

> [!NOTE]
> `groupadd` Command Syntax 
> 
> The general syntax for the `groupadd` command is as follows:
> 
> ```sh
> groupadd [OPTIONS] GROUPNAME
> ```
> 
> 
> Only the root or a user with [sudo](https://linuxize.com/post/sudo-command-in-linux/) privileges can create new groups.
> 
> When invoked, `groupadd` creates a new group using the options specified on the command line plus the default values specified in the [`/etc/login.defs`](http://man7.org/linux/man-pages/man5/login.defs.5.html) file.
> https://linuxize.com/post/how-to-create-groups-in-linux/

`$ sudo groupadd user42`

Create a new user and add it to the group:
It is possible to add the user to a group when creating the user:
`sudo useradd -g users USER`

Some distributions do not create a home directory, so the -m flag is required:
`sudo useradd -g users -m USER`

check the user exists and is in the right group(s)
`sudo id testuser`
Output should be something like:
![[09-id-user.png]]

Add the main user to the group:
`usermod -aG sudo USERNAME`

![[10-usermod.png]]



8. **Sudo Configuration**:
   - Limit sudo authentication to 3 attempts.
   - Display a custom message on sudo error due to wrong password.
   - Log all sudo actions to /var/log/sudo/.
   - Enable TTY mode for sudo.
   - Restrict sudo paths to: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin`.

SUDO:

1. Install `sudo`
    - install `sudo`, issue the command: `apt install sudo` (as root user)
2. Add users to `sudo`**group
    1. As `root` enter `usermod -aG sudo USERNAME`
3. ==**configure** sudo== following strict rules.
    - **Authentication**
        - Authentication using sudo has to be **limited to 3 attempts** in the event of an incorrect password.
            - `Defaults passwd_tries=3`
        - A **custom message** of your choice has to be displayed if an **error due to a wrong password** occurs when using `sudo`.
            - `Defaults badpass_message="Message of your choice!"
            - ![[11-sudoconfig.png]]
    - **Logging**
        - Each action using `sudo` has to be archived, both inputs and outputs. The log file has to be saved in the `/var/log/sudo/` folder.
            - `sudo mkdir /var/log/sudo`
        - Archive input and output events:
            - `%sudo ALL = (log_input, log_output) /usr/bin/sudo` The %sudo alias represents all users who can use sudo.
    - Security:
        - The TTY mode has to be enabled for security reasons.
            - `Defaults requiretty`
        - For security reasons too, the paths that can be used by sudo must be restricted. Example: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
        - `Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"`
	-  find - # User privilege specification, type `your_username ALL=(ALL) ALL`
    - ![[12-sudoconfig.png]]
![[13-sudoers_file.png]]

![[14-sudoers.png]]