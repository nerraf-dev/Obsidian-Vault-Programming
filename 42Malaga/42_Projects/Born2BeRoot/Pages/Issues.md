

Time Sync with host.

Various solutions, settings to be changed in VirtualBox etc.

### Using `chrony`

1. **Install `chrony`**:
   ```sh
   sudo apt update
   sudo apt install chrony
   ```

2. **Enable and start the `chrony` service**:
   ```sh
   sudo systemctl enable chrony
   sudo systemctl start chrony
   ```

3. **Check the status of the `chrony` service**:
   ```sh
   sudo systemctl status chrony
   ```

4. **Verify the time synchronization**:
   ```sh
   chronyc tracking
   ```

### Using `systemd-timesyncd`

If you prefer to use `systemd-timesyncd`, follow these steps:

1. **Enable and start `systemd-timesyncd`**:
   ```sh
   sudo systemctl enable systemd-timesyncd
   sudo systemctl start systemd-timesyncd
   ```

2. **Check the status of `systemd-timesyncd`**:
   ```sh
   sudo systemctl status systemd-timesyncd
   ```

3. **Verify the time synchronization**:
   ```sh
   timedatectl status
   ```
