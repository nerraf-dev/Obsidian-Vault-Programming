Once installation is complete, login as `root` and the user created during installation.

The new user needs to be added to the `sudo` group. First `sudo` needs to be installed using `apt` as the `root` user.

#### Install Sudo
Login as the root user.
Run `apt update && apt upgrade`. 
Then install `apt install sudo` 

Once installed, as `root` enter `usermod -aG sudo USERNAME` with USERNAME being whoever you want to add to the group.
Logout.

Log back in as the standard user to test `sudo`.

Login as the user created during install, eg newuser42. Try to switch to root. Try `sudo apt update`.


---
<<  [[03 - The Installation]] -|- [[05 - Creating a new group]] >>

