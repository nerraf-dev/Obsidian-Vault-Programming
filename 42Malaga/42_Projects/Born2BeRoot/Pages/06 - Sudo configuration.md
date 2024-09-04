
8. **Sudo Configuration**:
   - Limit sudo authentication to 3 attempts.
   - Display a custom message on sudo error due to wrong password.
   - Log all sudo actions to /var/log/sudo/.
   - Enable TTY mode for sudo.
   - Restrict sudo paths to: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin`.
---
First install `sudo`.
Switch to the root user and run: `apt install sudo` 

Once installed it is now possible to add our regular user (created during the installation) to the `sudo` group. As `root` enter `usermod -aG sudo USERNAME`

Configuring `sudo`can be completed using `visudo` but at the very top of the file it suggests adding the content to `/etc/sudoers.d/`

Create a new file  `touch /etc/sudoers.d/sudo_config`
Edit the file:
![[sudoers_config-file.png]]

Make sure the log directory exists, if not create it: `mkdir /var/log/sudo`

Can check is `sudo` is installed correctly by switching to root and running `sudo -V`
The output may be long so its worth outputting to a file, e.g. `sudo -V > output.txt`

![[sudo-v_output.png]]

---


![[14-sudoers.png]]




---
<<  [[05 - Creating a new group]] -|- [[07 - SSH & the firewall]] >>

