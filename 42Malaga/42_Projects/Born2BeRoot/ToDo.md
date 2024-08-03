### General Guidelines
1. **Virtualisation Tool**: Use VirtualBox (or UTM if VirtualBox is not available).
2. **Submission File**: Create a signature.txt file containing the signature of your machine’s virtual disk.

### Mandatory Part
1. **Operating System**: 
   - Choose and install the latest stable version of Debian (recommended) or Rocky.
   - Ensure SELinux (for Rocky) or AppArmor (for Debian) is running at startup and properly configured.

2. **System Setup**:
   - Do not install any graphical interface (X.org or equivalent).
   - Create at least 2 encrypted partitions using LVM.

3. **Knowledge Preparation**:
   - Understand the differences between aptitude and apt.
   - Know what SELinux or AppArmor is and how it works.

4. **SSH Configuration**:
   - Ensure SSH service runs on port 4242.
   - Disable root login via SSH.
   - Test SSH configuration with a new account.

5. **Firewall Configuration**:
   - Use UFW (Debian) or firewalld (Rocky) to open only port 4242.
   - Ensure the firewall is active at startup.

6. **Hostname Configuration**: Set the hostname to your login ending with 42 (e.g., wil42).

7. **Password Policy**:
   - Passwords expire every 30 days.
   - Minimum 2 days before a password can be modified.
   - Warning 7 days before password expiration.
   - Password must be at least 10 characters long, include uppercase, lowercase, and a number, and not have more than 3 consecutive identical characters.
   - Root password must comply with the same policy except it must have at least 7 characters not part of the former password.

8. **Sudo Configuration**:
   - Limit sudo authentication to 3 attempts.
   - Display a custom message on sudo error due to wrong password.
   - Log all sudo actions to /var/log/sudo/.
   - Enable TTY mode for sudo.
   - Restrict sudo paths to: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin`.

9. **User Management**:
   - ~~Create a user with your login as username belonging to user42 and sudo groups.~~
   - Be prepared to create a new user and assign it to a group during the defense.

10. **Monitoring Script**:
    - Create a bash script `monitoring.sh` to display system information every 10 minutes.
    - Information to display includes:
      - OS architecture and kernel version.
      - Number of physical and virtual processors.
      - Available RAM and its usage rate.
      - Available storage and its usage rate.
      - CPU usage rate.
      - Last reboot date and time.
      - LVM status.
      - Number of active connections.
      - Number of users logged in.
      - IPv4 and MAC address.
      - Number of commands executed with sudo.
    - Learn how to interrupt the script without modifying it.

### Bonus Part (only if mandatory part is perfect)
1. **Partition Setup**: Create a partition structure similar to the provided example.
2. **WordPress Setup**: Install and configure a WordPress website with lighttpd, MariaDB, and PHP.
3. **Additional Service**: Set up a useful service of your choice (excluding NGINX/Apache2) and justify your choice during the defense.
4. **Firewall Adjustment**: Adjust UFW/firewalld rules if additional services require opening more ports.

### Submission and Peer-Evaluation
1. **Retrieve Virtual Disk Signature**:
   - Windows: `certUtil -hashfile rocky_serv.vdi sha1`
   - Linux: `sha1sum rocky_serv.vdi`
   - Mac M1: `shasum rocky.utm/Images/disk-0.qcow2`
   - MacOS: `shasum rocky_serv.vdi`
2. **Submit Signature**: Paste the retrieved signature in the signature.txt file in the root of your Git repository.

---

