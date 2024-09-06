
> [!The Subject:]+
> Create a simple script called monitoring.sh. It must be developed in bash. At server startup, the script will display some information (listed below) on all terminals every 10 minutes (take a look at `wall`). The banner is optional. No error must be visible. 
> 
> Your script must always be able to display the following information: 
> - The architecture of your operating system and its kernel version. 
> - The number of physical processors. 
> - The number of virtual processors. 
> - The current available RAM on your server and its utilization rate as a percentage. 
> - The current available storage on your server and its utilization rate as a percentage. 
> - The current utilization rate of your processors as a percentage. 
> - The date and time of the last reboot. 
> - Whether LVM is active or not. 
> - The number of active connections. 
> - The number of users using the server. 
> - The IPv4 address of your server and its MAC (Media Access Control) address. 
> - The number of commands executed with the sudo program.


## Architecture:
The architecture of your operating system and its kernel version can be found using `uname`.

`uname -a`
Store it as a variable in the script
```bash
# ARCH
arch=$(uname -a)
```

### Physical Cores
The number of cores can be obtained from the file `/proc/cpuinfo`. 
![[proc_cpuinfo.png]]
`cpuinfo` is a text file, so it is easiest to [[`grep`]] 
`grep 'physical id' /proc/cpuinfo | sort | uniq | wc -l`

`phys_cores=$(grep "physical id" /proc/cpuinfo | wc -l)`
### Virtual Processors
The number of virtual processors.

`grep 'processor' /proc/cpuinfo | cut -d':' -f2 | sort -n | uniq -c | awk '{print $1}'`

This command is a pipeline of several commands used to process and extract information about the CPU processors from the `/proc/cpuinfo` file in a Unix-like operating system. Here's a step-by-step explanation:

1. **`grep 'processor' /proc/cpuinfo`**:
    
    - Searches for lines containing the word "processor" in the `/proc/cpuinfo` file. This file contains detailed information about the CPU.
2. **`cut -d':' -f2`**:
    
    - Cuts each line at the colon (`:`) delimiter and selects the second field. This extracts the processor number.
3. **`sort -n`**:
    
    - Sorts the extracted processor numbers numerically.
4. **`uniq -c`**:
    
    - Counts the number of occurrences of each unique processor number.
5. **`awk '{print $1}'`**:
    
    - Uses `awk` to print only the first field of each line, which is the count of each unique processor number.


`virt_cpu = $(grep 'processor' /proc/cpuinfo | cut -d':' -f2 | sort -n | uniq -c | awk '{print $1}')`
### RAM
The current available RAM on your server and its utilisation rate as a percentage.
Use `free`.

```bash
free --mega
               total        used        free      shared  buff/cache   available
Mem:            1007         213         817           0          99         794
Swap:           1023           0        1023


free -h
               total        used        free      shared  buff/cache   available
Mem:           960Mi       203Mi       779Mi       604Ki        95Mi       757Mi
Swap:          975Mi          0B       975Mi


```
The output above shows free with two simple options `--mega` and `-h`.
`--mega` displays the output in Megabytes (and so implies SI units).
`-h` Show all output fields automatically scaled to shortest three digit unit and display the units of print out. Following units are used.
 ```
		B = bytes
		Ki = kibibyte
		Mi = mebibyte
		Gi = gibibyte
		Ti = tebibyte
		Pi = pebibyte
```

Get **available** RAM:
`free --mega | awk '$1=="Mem:" {print $7}'`

Used:
`free --mega | awk '$1=="Mem:" {print $3}'`

Total:
`free --mega | awk '$1=="Mem:" {print $2}'`


- `free --mega` 
	- Runs the `free` command with the `--mega` option, which displays memory usage in megabytes.
- **`awk '$1=="Mem:" {print $3}'`**:
    - Uses `awk` to process the output of the `free` command.
    - `$1=="Mem:"` filters the lines to only process the line where the first field is "Mem:".
    - `{print $3}` prints the third field of the filtered line, which corresponds to the used memory in megabytes.



### Disk Storage

> [!NOTE]
> The current available storage on your server and its utilisation rate as a percentage.
> 

To get this information, use the `df` command. It provides an onscreen summary of the filesystem.

```bash
df -h --total
Filesystem                      Size  Used Avail Use% Mounted on
udev                            457M     0  457M   0% /dev
tmpfs                            97M  604K   96M   1% /run
/dev/mapper/sfarren42--vg-root  2.5G  1.3G  1.1G  54% /
tmpfs                           481M     0  481M   0% /dev/shm
tmpfs                           5.0M     0  5.0M   0% /run/lock
/dev/mapper/sfarren42--vg-var   1.2G  264M  795M  25% /var
/dev/mapper/sfarren42--vg-tmp   253M  8.0K  235M   1% /tmp
/dev/mapper/sfarren42--vg-home  6.4G   80K  6.1G   1% /home
/dev/sda1                       455M  109M  322M  26% /boot
tmpfs                            97M     0   97M   0% /run/user/1000
total                            12G  1.6G  9.6G  15% -

```
the `--total` flag add the additional total row. 

**Available disk space:**  `df -h --total | awk '$1 == "total" {print $4}'`
**Utilisation rate as a percentage:** `df -h --total | awk '$1 == "total" {print $5}'`

### CPU Usage
The current utilisation rate of your processors as a percentage.
```bash
# CPU USAGE
cpu_idle=$(vmstat 1 3 | tail -1 | awk '{print $15}')
cpu_usage=$(awk "BEGIN {print 100 - $cpu_idle}")%

```

`cpu_idle` access the value from `vmstat` after a short delay.
`cpu_usage` generates the final percentage value.

The first line of the script, `cpu_idle=$(vmstat 1 3 | tail -1 | awk '{print $15}')`, uses the `vmstat` command to gather system performance statistics. 
- The `vmstat 1 3` command runs `vmstat` three times at one-second intervals. The output of `vmstat` includes various system metrics, with each line representing a snapshot of the system's state at a given time. 
- The `tail -1` command extracts the last line of this output, which represents the most recent snapshot. 
- The `awk '{print $15}'` command then extracts the 15th field from this line, which corresponds to the percentage of CPU time that is idle.

The second line, `cpu_usage=$(awk "BEGIN {print 100 - $cpu_idle}")%`, calculates the CPU usage by subtracting the idle percentage from 100. This is done using the `awk` command in a `BEGIN` block, which allows for the execution of an arithmetic operation before processing any input lines. The result is stored in the `cpu_usage` variable and represents the percentage of CPU time that is actively being used. The trailing % symbol is appended to indicate that the value is a percentage.

### Last Reboot
The date and time of the last reboot.

```bash
last reboot | head -1 | awk '{print $5}'

last reboot | head -1 | awk '{print $5 $6 $7 $8}'
```

 `last reboot`, which lists the reboot history of the system. Each line of the output represents a reboot event, including the date and time of the reboot. The `head -1` command is then used to select the first line of this output, which corresponds to the most recent reboot event.

Next, the `awk '{print $5, $6, $7, $8}'` command processes this line to extract specific fields. In this context, the fields `$5`, `$6`, `$7`, and `$8` typically represent the date and time of the reboot. The `awk` command prints these fields, effectively formatting the timestamp of the last reboot.


alternative: 
```bash
who -b | awk '$1 == "system" {print $3, $4, $5}'
```
### LVM Active
Whether LVM is active or not.

```bash
lsblk | grep -q "lvm" && echo "yes" || echo "no"
```

1. `lsblk`:
    - The `lsblk` command lists information about all available or the specified block devices. It provides details such as the device name, size, type, and mount point.
2. **`grep -q "lvm"`**:
    
    - The output of `lsblk` is piped (`|`) to the `grep` command.
    - The `-q` option makes `grep` operate in "quiet" mode, where it does not output any lines but sets the exit status to 0 if a match is found and to 1 if no match is found.
    - The string `"lvm"` is the pattern that `grep` searches for in the `lsblk` output. If any of the block devices are part of an LVM volume group, `lsblk` will include "lvm" in its output.
3. **`&& echo "yes"`**:
    
    - The `&&` operator is a logical AND. It means that the command following it (`echo "yes"`) will only be executed if the preceding command (`grep -q "lvm"`) succeeds (i.e., finds a match and exits with status 0).
    - If `grep` finds "lvm" in the `lsblk` output, `echo "yes"` is executed, indicating that LVM is active.
4. **`|| echo "no"`**:
    - The `||` operator is a logical OR. It means that the command following it (

### Active Connections (TCP)
The number of active connections.

```bash
ss -t | grep -i estab* | wc -l
```

### Current Users
The number of users using the server.
```bash
users=$(who | wc -l)
```
### IP & MAC
The IPv4 address of your server and its MAC (Media Access Control) address.

### `sudo` Count
The number of commands executed with the sudo program.


---
### Complete Script:
```bash
#!/bin/bash

# ARCHITECTURE
# The architecture of your operating system and its kernel version.
arch=$(uname -a)

# CPU INFO
# The number of physical processors.
# The number of virtual processors.
physical=$(grep "physical id" /proc/cpuinfo | wc -l)
virtual=$(grep 'processor' /proc/cpuinfo | cut -d':' -f2 | sort -n | uniq -c | awk '{print $1}')


# RAM
# The current available RAM on your server and its utilization rate as a percentage.
total_ram=$(free --mega | awk '$1=="Mem:" {print $2}')
used_ram=$(free --mega | awk '$1=="Mem:" {print $3}')
available_ram=$(free --mega | awk '$1=="Mem:" {print $7}')
ram_utilization=$(free --mega | awk '$1 == "Mem:" {printf("(%.2f%%)\n", $3/$2*100)}')

# STORAGE
# The current available storage on your server and its utilization rate as a percentage.
total_storage=$(df -h --total | awk '$1=="total" {print $2}')
available_storage=$(df -h --total | awk '$1=="total" {print $4}')
disk_usage=$(df -h --total | awk '$1=="total" {print $5}')

# CPU USAGE
# The current utilization rate of your processors as a percentage.
cpu_idle=$(vmstat 1 3 | tail -1 | awk '{print $15}')
cpu_usage=$(awk "BEGIN {print 100 - $cpu_idle}")%

# LAST BOOT
# The date and time of the last reboot.
last_boot=$(last reboot | head -1 | awk '{print $5, $6, $7, $8}')

# LVM USE
# Whether LVM is active or not.
lvm_active=$(lsblk | grep -q "lvm" && echo "yes" || echo "no")

# CONNECTIONS TCP
# The number of active connections.
tcp_connections=$(ss -t | grep -i ESTAB | wc -l)

#USER LOG
# The number of users using the server.
users=$(who | wc -l)

# NETWORK IP & MAC
# The IPv4 address of your server and its MAC (Media Access Control) address.
ip_address=$(ip -o -4 addr show | grep -v '127.0.0.1' | awk '{print $4}')
mac_address=$(ip link show | awk '/ether/ {print $2}')

# SUDO COMMANDS
# The number of commands executed with the sudo program.
sudo_commands=$(journalctl -q _COMM=sudo | grep COMMAND | wc -l)

# The number of commands executed with the sudo program.
# sudo_log="/var/log/sudo/sudo_log"
# if sudo [ -f "$sudo_log" ]; then
#     sudo_commands=$(sudo grep -c "COMMAND=" "$sudo_log")
# else
#     sudo_commands="Log file not found"
# fi

# Display information using wall
wall <<EOF
+--------------------------------------------------+
|                System Information                |
+--------------------------------------------------+

Architecture:   $arch
Physical CPUs:  $physical
Virtual CPUs:   $virtual
Memory Usage:   $used_ram/${total_ram}MB $ram_utilization
Disk Usage:     $disk_usage
CPU Load:       $cpu_usage
Last Boot:      $last_boot
LVM Use:        $lvm_active
TCP Connections:$tcp_connections
User log:       $users
Network:        $ip_address ($mac_address)
Sudo Commands: $sudo_commands cmds
EOF
```


### Crontab
What is crontab?It is a background process manager. The specified processes will be executed at the time you specify in the crontab file.

To properly configure crontab, we must edit the crontab file with the following command `sudo crontab -u root -e`.

In the file, we must add the following command for the script to execute every 10 minutes
```bash
# Run sysinfo.sh every 10 minutes
# m h dom mon dow
*/10 * * * * sh  /home/sfarren/sys-msg/sysinfo.sh
```
Operation of each crontab parameter:

m ➤ Corresponds to the minute at which the script will be executed, the value ranges from 0 to 59.

h ➤ The exact hour, the 24-hour format is used, the values range from 0 to 23, with 0 being 12:00 midnight. dom ➤ refers to the day of the month, for example, you can specify 15 if you want to execute every day 15.

dow ➤ means the day of the week, it can be numeric (0 to 7, where 0 and 7 are Sunday) or the first three letters of the day in English: mon, tue, wed, thu, fri, sat, sun.

user ➤ Defines the user who will execute the command, it can be root, or another user as long as it has permission to execute the script.

command ➤ Refers to the command or the absolute path of the script to be executed.



---
### Install and Configure NTP

#### For Debian/Ubuntu:

1. **Install `ntp`**:
    
	```
	sudo apt-get update
	sudo apt-get install ntp systemd-timesyncd
	```
    
2. **Enable and Start the NTP Service**:
	```
	sudo systemctl enable ntp
	sudo systemctl start ntp
	```
	    

```bash
sudo systemctl enable ntp
sudo systemctl start ntp
sudo systemctl enable systemd-timesyncd
sudo systemctl start systemd-timesyncd
```

---
<<  [[08 - Password Policy]] -|-  -- >>