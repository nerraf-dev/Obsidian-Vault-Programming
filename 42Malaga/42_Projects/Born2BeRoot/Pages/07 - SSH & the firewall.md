
4. **SSH Configuration**:
   - [ ] Ensure SSH service runs on port 4242.
   - [ ] Disable root login via SSH.
   - [ ] Test SSH configuration with a new account.

**Firewall Configuration**:
   - [ ] Use UFW (Debian) or firewalld (Rocky) to open only port 4242.
   - [ ] Ensure the firewall is active at startup.

Install UFW:
```bash
sudo apt install ufw
```

Some networking issues! Make sure the VM is set to used a bridged adapter, so that it gets an IP address.

**Set default policies to deny incoming and allow outgoing traffic**:
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Allow SSH on port 4242:
```bash
sudo ufw allow 4242/tcp
```

Enable ufw:
```bash
sudo ufw enable
```

### Configure sshd
Edit sshd_config
```bash
sudo nano /etc/ssh/sshd_config
```

#### Modify the settings 
Change `# Port 22` to `Port 4242`

The root user should not be able to login, the line `PermitRootLogin prohibit-password` will allow the root user to login using a correct key.

Change this to: `PermitRootLogin no`

Save...
Restart sshd and then check it has started up and listening on the correct port
```bash
sudo systemctl restart sshd
sudo systemctl status sshd
```


---
<<  [[06 - Sudo configuration]] -|- -- >>