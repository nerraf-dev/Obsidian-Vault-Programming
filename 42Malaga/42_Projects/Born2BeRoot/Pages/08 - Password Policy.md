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

![[password_aaging.png]]

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
```bash
sudo nano /etc/pam.d/common-password
```

Need to look for the line ending `retry=3`
and add 

![[password_policy.png]]

The line is long, the screenshot show word wrapping.


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
<<  [[07 - SSH & the firewall]] -|- [[09 - The Script]] -- >>