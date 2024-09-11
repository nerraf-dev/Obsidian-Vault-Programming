```bash
who -b && uptime && date && last sfarren | head -n 1
         system boot  2024-09-11 16:01
 16:06:17 up 9 min,  2 users,  load average: 0.01, 0.06, 0.02
Wed 11 Sep 16:06:17 CEST 2024
sfarren  pts/0        10.13.8.1        Wed Sep 11 16:02   still logged in
```

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
