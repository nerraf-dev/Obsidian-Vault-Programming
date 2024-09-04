#### Create a new group
*Create a new group `user42` and add the existing user and new user to it.* 

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

Add user to the user42 group:
`usermod -aG user42 USERNAME`
#### Create a new user and add it to the group:
It is possible to add the user to a group when creating the user using the command:
```bash
sudo useradd -g user42 USER
```

Some distributions do not create a home directory, so the `-m `flag is required:
```bash
sudo useradd -g user42 -m USER
```

**Check the user exists and is in the right group(s)**
`sudo id testuser`

Output should be something like:
![[09-id-user.png]]

Show all users by `sudo cat /etc/passwd`

**To add a user to the `sudo` group:**
`usermod -aG sudo USERNAME`

![[10-usermod.png]]



---
<<  [[04 - Logging In & Setting Up]] -|- [[06 - Sudo configuration]] >>

