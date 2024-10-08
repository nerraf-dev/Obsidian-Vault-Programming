**Password Policy**:
   - [ ] Passwords expire every 30 days.
   - [ ] Minimum 2 days before a password can be modified.
   - [ ] Warning 7 days before password expiration.
   - [ ] Password must be at least 10 characters long, include uppercase, lowercase, and a number, and not have more than 3 consecutive identical characters.
   - [ ] Root password must comply with the same policy except it must have at least 7 characters not part of the former password.

Begin by editing the `login.defs` file:
```bash
sudo nano /etc/login.defs
```

Once open it's time to start modifying:

![[password_aging.png]]

Look for:
```
PASS_MAX_DAYS    9999
PASS_MIN_DAYS    0
PASS_WARN_AGE    7
```
Change to:
```
PASS_MAX_DAYS    30
PASS_MIN_DAYS    2
PASS_WARN_AGE    7
```

Save and exit to the terminal. 
Additional packages are required:
```bash
sudo apt install libpam-pwquality
```

Now some settings need editing:

Then, edit the `/etc/security/pwquality.conf` file like so:

```shell
# Number of characters in the new password that must not be present in the 
# old password.
difok = 7
# The minimum acceptable size for the new password (plus one if 
# credits are not disabled which is the default)
minlen = 10
# The maximum credit for having digits in the new password. If less than 0 
# it is the minimun number of digits in the new password.
dcredit = -1
# The maximum credit for having uppercase characters in the new password. 
# If less than 0 it is the minimun number of uppercase characters in the new 
# password.
ucredit = -1
# ...
# The maximum number of allowed consecutive same characters in the new password.
# The check is disabled if the value is 0.
maxrepeat = 3
# ...
# Whether to check it it contains the user name in some form.
# The check is disabled if the value is 0.
usercheck = 1
# ...
# Prompt user at most N times before returning with error. The default is 1.
retry = 3
# Enforces pwquality checks on the root user password.
# Enabled if the option is present.
enforce_for_root
# ...
```

Change user passwords to comply with password policy:

```shell
$ sudo passwd <user/root>
```

---
~~alternative:~~
```bash
sudo nano /etc/pam.d/common-password
```

~~Need to look for the line ending `retry=3`~~
~~and add~~ 

~~![[password_policy.png]]~~

~~The line is long, the screenshot show word wrapping.~~


**The commands:**
- `minlen=10` --> The minimum number of characters a password must contain.
- `ucredit=-1` --> Uppercase letters required. -1 means at least 1 u/case char. 
- `lcredit=-1` --> Must contain at least one lowercase letter
- `dcredit=-1` --> Must contain at least one digit
- `maxrepeat=3` --> The same character **cannot** be repeated more than three times continuously.
- `reject_username` --> Can not contain the username inside itself.
- `difok=7` --> Has to contain at least seven different characters from the last password used.
- `enforce_for_root` --> We will implement this password policy to root.
---

New users created will now have to adhere to this password policy. 
But for the root user and login user we create at the beginning, we need to manually change the time setting of days between password chagne.

Use command: `sudo chage -l <username>` to check the password of root and login user.

The min/max days between password change are still set as the default, as the users we added before the policy was created.

![[root_pwd_check.png]]

We need to use command: `sudo chage -m <time> <username>` and `sudo chage -M <time> <username>` to modify the days between password change.

-m is minimun days, should be 2 days; -M is maximun days, shoule be 30 days.

![[pwd-check.png]]

---
<<  [[07 - SSH & the firewall]] -|- [[09 - Connect Via SSH]] -- >>