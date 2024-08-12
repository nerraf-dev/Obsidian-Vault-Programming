
8. **Sudo Configuration**:
   - Limit sudo authentication to 3 attempts.
   - Display a custom message on sudo error due to wrong password.
   - Log all sudo actions to /var/log/sudo/.
   - Enable TTY mode for sudo.
   - Restrict sudo paths to: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin`.

1. Install `sudo`
    - install `sudo`, issue the command: `apt install sudo` (as root user)
2. Add users to `sudo`**group
    1. As `root` enter `usermod -aG sudo USERNAME`
3. ==**configure** sudo== following strict rules, using `sudo visudo` to modify the sudoers file
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


![[14-sudoers.png]]




---
<<  [[05 - Creating a new group]] -|- [[07 - SSH & the firewall]] >>

