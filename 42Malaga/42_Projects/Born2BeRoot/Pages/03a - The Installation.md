****### The Install
Start the VM and follow the process.
"Do not install any graphical interface (X.org or equivalent)" So use the **Install** option
![[02-Installer.png]]
Go through localisation options.

> [!NOTE]
> **Hostname Configuration**: Set the hostname to **your login** ending with 42 (e.g., wil42).

The installer provides an option to set the **hostname**. It can be checked and edited again later via the [[hosts file]]. 
![[03-Installer-Hostname.png]]

Set the `root` password.

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

The installer will create a non-admin user. This means that the user management part can be started. Create the new user as the 42 username

![[04-Installer-NewUser.png]]

Set the user name and password as per the requirements.

```text
User: sfarren
Pass: 123ABCdef0
```


[[03b - Partitioning]]

   - ***Create at least 2 encrypted partitions using LVM.***
   - 
Pick Use entire disk and set up encrypted LVM
![[05-Installer-LVM.png]]

Selecting this option creates 3 partitions on the LVM encrypted volume
![[06-Installer-Partitions.png]]

The drive requires an encryption passphrase, enter this during install.

Passphrase: `123ABCdef0`

Allow the max size for partitioning and follow along.

The installer shows how the drive will be setup:
![[07-Drive setup.png]]
It shows two drives, with one of them being encrypted. 
![[08-partitions.png]]


The installer continues. When presented with a choice of install options I turned it all off to avoid anything unwanted being installed. However this does mean there is no `sudo` or `net-tools` and some other commonly used Linux tools! These will need installing using `apt`.

The installer can setup SSH, but in this attempt I will go through installing it myself with `apt`. Other tools need installing such as `sudo` and `ufw`.


---
<<  [[02 - The OS]] -|- [[04 - Logging In & Setting Up]] >>

[[00 - Walkthrough]]
