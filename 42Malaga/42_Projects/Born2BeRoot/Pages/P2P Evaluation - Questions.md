https://42-cursus.gitbook.io/guide/rank-01/born2beroot/p2p-evaluation-questions

Be careful, the first check that the student is going to do is checking that in your git repo there is only the signature of your virtual machine and NOTHING else. The signature must be identical as the one on your VM at the time of the evaluation (if you change something on your VM afterwards, the signature will be different).

## 

[](https://42-cursus.gitbook.io/guide/rank-01/born2beroot/p2p-evaluation-questions#theoretical-questions)

Theoretical questions

Here are the **theoretical questions** you will be asked during the evaluation:

- How does a virtual machine work ? And what its purpose ?
    
- Wh did you choose Debian or CentOS ?
    
- What's the difference between Debian and CentOS ?
    
    - If you chose Debian: what's the difference between aptitude, apt and what's APPArmor ?
        
    - If you chose CentOS: what's SELinux and DNF ?
        
    
- What the advantages/disadvantages of a strong password policy ? What can you say about its implementation ?
    
- What's a partition ? And more generally how does LVM (Logical Volume Management) work ?
    
- What's sudo ?
    
- What's an UFW and what's the value of using it ?
    
- What's SSH (Secure Shell) and what's the value of using it ?
    
- What is cron ?
    

Everything (and even more than necessary) is explained here:

[📠What's a virtual machine ?](https://42-cursus.gitbook.io/guide/rank-01/born2beroot/whats-a-virtual-machine)[📠Install your virtual machine](https://42-cursus.gitbook.io/guide/rank-01/born2beroot/install-your-virtual-machine)

## 

[](https://42-cursus.gitbook.io/guide/rank-01/born2beroot/p2p-evaluation-questions#practical-questions)

Practical questions

And here are the **practical questions** that you will be asked to demonstrate and the command that you need to write to get to the answer:

- Check that the signature contained is identical to that of the ".vdi" file of the virtual machine to be evaluated.
    
    1. Open iTerm and type `cd`
        
    2. Then type `cd sgoinfre/students/<your_intra_username>/<file of your VM>`
        
    3. Then type `shasum VirtualBox.vdi` (or any other name that your VM has .vdi)
        
    
- During the evaluation a script must display information every 10 minutes
    

![](https://42-cursus.gitbook.io/~gitbook/image?url=https%3A%2F%2F2977649544-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fz2zo8aAL0o31034sj7J7%252Fuploads%252FELWAEe1hW58NJ6jHOnPQ%252Fimage.png%3Falt%3Dmedia%26token%3D3b1e68cf-65d5-4ece-9629-7ea424e0d539&width=768&dpr=4&quality=100&sign=c536c35d&sv=1)

Script that should appear every 10 minutes

- The machine should not have a graphical environment at launch.
    
- A password is requested before attempting to connect to this machine.
    
- You need to connect with an user. The user must not be root.
    
- Check that the UFW service is started
    
    - `sudo ufw status`
        
    
- Check that the SSH service is started
    
    - `sudo systemctl status ssh`
        
    

![](https://42-cursus.gitbook.io/~gitbook/image?url=https%3A%2F%2F2977649544-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fz2zo8aAL0o31034sj7J7%252Fuploads%252FaMQldwLnoWbjxqosCgiZ%252Fimage.png%3Falt%3Dmedia%26token%3Dc05bfc9d-6b01-4040-adde-60637775dc70&width=768&dpr=4&quality=100&sign=536cbe61&sv=1)

you will find the status of the ssh service

- Check that the operating system is Debian or CentOS (you can check it on the information script that is displayed every 10 minutes)
    
- Check that a user with your login exists and is present on your VM. This user should belong to the groups "sudo" and "user42".
    
    - `getent group sudo`
        
    - `getent group user42`
        
    
    ![](https://42-cursus.gitbook.io/~gitbook/image?url=https%3A%2F%2F2977649544-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fz2zo8aAL0o31034sj7J7%252Fuploads%252F9sbUiN3uMiOd2t0vYGic%252Fimage.png%3Falt%3Dmedia%26token%3D68f5b44c-bcbf-420d-88f4-bd0a460f6127&width=768&dpr=4&quality=100&sign=a5c842b2&sv=1)
    
- Make sure that the rules imposed in the subject concerning the password policy have been put in place by following these steps:
    
    - Create a new user for the evaluator: `sudo adduser <new_username>`
        
    - He/She chooses a password
        
    - Create a new group named "evaluating": `sudo groupadd <groupname>`
        
    - Assign it to your new user (the evaluator's user): `sudo usermod -aG <groupname> <username>`
        
    - Check the password expire rules: `sudo chage -l username`
        
    
    ![](https://42-cursus.gitbook.io/~gitbook/image?url=https%3A%2F%2F2977649544-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fz2zo8aAL0o31034sj7J7%252Fuploads%252FzJYRhKR5uMfsMapBEyfl%252Fimage.png%3Falt%3Dmedia%26token%3Db6017a16-42c8-46ac-8253-36a6a63bf201&width=768&dpr=4&quality=100&sign=862c8835&sv=1)
    
    your password rules should look like this
    
- Check that this new user belongs to the "evaluating" group: `getent group evaluating`
    
- Check that the hostname of the machine is correctly formatted as follows: login42
    
    - `hostnamectl`
        
    
- Modify this hostname by replacing the login with yours, then restart the machine (the new host name should be updated)
    
    - `hostnamectl set-hostname <new_hostname>`
        
    - change the hostname in this file too: `sudo nano /etc/hosts`
        
    - Restart your virtual machine
        
    
- Restore the machine to the original name (just do the same thing as above)
    
- Check the partitions for your VM (compare the output with the example in the subject).
    
    - `lsblk`
        
    
- Check that the sudo program is properly installed on the virtual machine
    
    - `dpkg -l | grep sudo –`
        
    
- Assign the evaluator's username to the "sudo" group
    
    - `sudo usermod -aG <groupname> <username>`
        
    
- Verify that the " /var/log/sudo/" folder exists and hast at least one file.
    
    - `cd /var/log/sudo/`
        
    
- Check the contents of the files in this folder. You should see a history of the command used with sudo.
    
    - `ls` to check what contains this folder
        
    - `cat sudo.log` (this file is the file with the history of sudo commands)
        
    
- Try to run a command via sudo and see if the files above have been updated
    
    - write whatever you want (i.e. sudo ls) and check if the new log has been added to the history by reading the file again (`cat sudo.log`)
        
    
- Check that the UFW program is installed on your VM and that is working properly
    
    - `dpkg -l | grep ufw –`
        
    
- List the active rule in UFW. A rule must exist for port 4242.
    
    - `sudo ufw status numbered`
        
    
    ![](https://42-cursus.gitbook.io/~gitbook/image?url=https%3A%2F%2F2977649544-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fz2zo8aAL0o31034sj7J7%252Fuploads%252Fg70XOpWpQAqqPzi2I65l%252Fimage.png%3Falt%3Dmedia%26token%3De688b4ef-3e19-4e91-a8ee-d088fadc79d2&width=768&dpr=4&quality=100&sign=340d5eb8&sv=1)
    
- Add a new rule to open port 8080
    
    - `sudo ufw allow 8080`
        
    
- Check that it has been added to the active rules
    
    - `sudo ufw status numbered`
        
    
- Delete this new added rule.
    
    - `sudo ufw delete <rule_number>` (mine is 2 and then i do it again with 3)
        
    
- Check that the SSH service is installed and working on your virtual machine
    
    - `dpkg -l | grep ssh –`
        
    
- Verify that the SSH service only uses port 4242
    
    - Open your iTerm
        
    - write: `ssh your_user_id@127.0.0.1 -p 4242`
        
    - You are now connected on your VM through your terminall
        
    
- Make sure that you cannot user SSH with the "root" user
    
- Open your information script (the one that appears every 10 minutes) and explain it
    
    - if you followed the same github guide as me just type: `cd /usr/local/bin/`
        
    - and then: `cat monitoring.sh`
        
    

Explanation for monitoring.sh[](https://42-cursus.gitbook.io/guide/rank-01/born2beroot/p2p-evaluation-questions#explanation-for-monitoring.sh)

- Change the cron and to make sure that your informative script appears now every minute
    
    - Type `sudo crontab -u root -e` to open the crontab and add the rule
        
    - New rule: `*/1 * * * *`
        
    - Restart the server one last time