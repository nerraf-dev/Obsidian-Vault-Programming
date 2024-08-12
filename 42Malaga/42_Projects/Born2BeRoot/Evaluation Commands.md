 #### **1. Verify No Graphical Interface is Running**

We'll use the command `ls /usr/bin/*session` and the output should match the screenshot. If there's a difference, a graphical interface is likely in use.

#### **2. Verify UFW Service is Active**

Bash

```
sudo ufw status
sudo service ufw status
```


#### **3. Verify SSH Service is Active**

Bash

```
sudo service ssh status
```


#### **4. Verify Operating System is Debian or CentOS**

Bash

```
uname -v
uname --kernel-version
```

#### **5. Verify User is in "sudo" and "user42" Groups**

Bash

```
getent group sudo
getent group user42
```


#### **6. Create a New User and Verify Password Policy**

Bash

```
sudo adduser name_user
```


Enter a password that adheres to the policy.

#### **7. Create a New Group Named "evaluating"**

Bash

```
sudo addgroup evaluating
```

#### **8. Add the New User to the New Group**

Bash

```
sudo adduser name_user evaluating
```


#### **9. Verify Hostname is Correctly Set to login42**



#### **10. Modify Hostname to Replace Your Login with Evaluator's (e.g., student42)**

Edit `/etc/hostname` and `/etc/hosts` to replace your login with `student42`. Restart the machine.


