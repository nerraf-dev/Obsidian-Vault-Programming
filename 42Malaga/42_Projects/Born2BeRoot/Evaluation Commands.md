 #### **1. Verify No Graphical Interface is Running**

We'll use the command `ls /usr/bin/*session` and the output should match the screenshot. If there's a difference, a graphical interface is likely in use.

 [![Image of command output](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcQMldOv6lkeNaZjBHEnSE6SmD7jMO5nR9tCoGx6BnwEkTwz6Qr8KSt0HmiyW2oV) Opens in a new window](https://www.geeksforgeeks.org/how-to-save-output-of-command-in-a-file-in-linux/) [![](https://encrypted-tbn1.gstatic.com/favicon-tbn?q=tbn:ANd9GcRhozPFEmg8f-ipzeQviUztsisaCXzxmMiAMrRliVhPQtJyEMMq_0b1osZy_EdZwXvGx2s17j-bfdCt94tYx_ITDG-xKXoZ_BxsQE05uyyO)www.geeksforgeeks.org](https://www.geeksforgeeks.org/how-to-save-output-of-command-in-a-file-in-linux/)

command output 

#### **2. Verify UFW Service is Active**

Bash

```
sudo ufw status
sudo service ufw status
```

Use code [with caution.](/faq#coding)

 [![Image of command outputs](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQWxPOoM2y2pBK1aeEyOSxljygBL0rcfPts912SZh-YVgU1iq62ZosOTSdRTiTI) Opens in a new window](https://www.tecmint.com/save-command-output-to-a-file-in-linux/) [![](https://encrypted-tbn1.gstatic.com/favicon-tbn?q=tbn:ANd9GcQDHtCrri-QH3UEjI7lJLRxSm-UwEYf1qjcocmmBV8xgC3GLUE8GM0RfEQ-FJwkPbOdceCFG2oB6q_HeVXOlHTnLwlwmuCnY21u)www.tecmint.com](https://www.tecmint.com/save-command-output-to-a-file-in-linux/)

command outputs 

#### **3. Verify SSH Service is Active**

Bash

```
sudo service ssh status
```

Use code [with caution.](/faq#coding)

 [![Image of command output](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcQcTcV5fHgSpn9MOfbUjjggWb-yLkEd2CAuophmH6LVdf--RlDRPZNWge99fsFp) Opens in a new window](https://stackoverflow.com/questions/7318497/omitting-the-first-line-from-any-linux-command-output) [![](https://encrypted-tbn0.gstatic.com/favicon-tbn?q=tbn:ANd9GcSZCmAD8gauBz6zQWhiwNyTdW_qTaFn86kY4i9ue0TKLdig0zZecaQOGXjB62-l1zYTQFINdpkKZYc51ilBK8hviR3QOYWdHDC9F54)stackoverflow.com](https://stackoverflow.com/questions/7318497/omitting-the-first-line-from-any-linux-command-output)

command output 

#### **4. Verify Operating System is Debian or CentOS**

Bash

```
uname -v
uname --kernel-version
```

Use code [with caution.](/faq#coding)

 [![Image of command output](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcTxmzmSZmBBvf1BsOw-Q1cfcp8F5badiK6Hu7T3Sa0rDaCf2aWb-v9TWQJGlJc6) Opens in a new window](https://www.tecmint.com/save-command-output-to-a-file-in-linux/) [![](https://encrypted-tbn1.gstatic.com/favicon-tbn?q=tbn:ANd9GcQDHtCrri-QH3UEjI7lJLRxSm-UwEYf1qjcocmmBV8xgC3GLUE8GM0RfEQ-FJwkPbOdceCFG2oB6q_HeVXOlHTnLwlwmuCnY21u)www.tecmint.com](https://www.tecmint.com/save-command-output-to-a-file-in-linux/)

command output 

#### **5. Verify User is in "sudo" and "user42" Groups**

Bash

```
getent group sudo
getent group user42
```

Use code [with caution.](/faq#coding)

 [![Image of command output](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRISzr-iRzUajl2XyZB2ogMS0UyjyksnmbQpg8wuOJ0Q8PVkLNAsPBTodgLXpui) Opens in a new window](https://stackoverflow.com/questions/37933003/command-prompt-read-system-output) [![](https://encrypted-tbn0.gstatic.com/favicon-tbn?q=tbn:ANd9GcSZCmAD8gauBz6zQWhiwNyTdW_qTaFn86kY4i9ue0TKLdig0zZecaQOGXjB62-l1zYTQFINdpkKZYc51ilBK8hviR3QOYWdHDC9F54)stackoverflow.com](https://stackoverflow.com/questions/37933003/command-prompt-read-system-output)

command output 

#### **6. Create a New User and Verify Password Policy**

Bash

```
sudo adduser name_user
```

Use code [with caution.](/faq#coding)

Enter a password that adheres to the policy.

 [![Image of command output](https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcS7hSbK11-_UWuyqy20_MPSEnVsWs_8SP_fqZ8LbPQzAcjfLlwVRF7qMHcZHjkH) Opens in a new window](https://helpdeskgeek.com/how-to/redirect-output-from-command-line-to-text-file/) [![](https://encrypted-tbn2.gstatic.com/favicon-tbn?q=tbn:ANd9GcTwDV1r35OPqe9h4CZmUnnZJC1KxTvdBdbZUJp0n3Jh4CVuId4IHd4jL632ZuROVk2lUPVT8nvvLnZNAzDhLgvK33NfUkaFwtJGzg)helpdeskgeek.com](https://helpdeskgeek.com/how-to/redirect-output-from-command-line-to-text-file/)

command output 

#### **7. Create a New Group Named "evaluating"**

Bash

```
sudo addgroup evaluating
```

Use code [with caution.](/faq#coding)

 [![Image of command output](https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcT-vcCBEwPCcIe2vOCA6W8GyUM2iMiRL_njfZjSzRwGdGACoTZhO0hb3nh5eZEY) Opens in a new window](https://stackoverflow.com/questions/21080368/put-output-of-command-prompt-to-clipboard) [![](https://encrypted-tbn0.gstatic.com/favicon-tbn?q=tbn:ANd9GcSZCmAD8gauBz6zQWhiwNyTdW_qTaFn86kY4i9ue0TKLdig0zZecaQOGXjB62-l1zYTQFINdpkKZYc51ilBK8hviR3QOYWdHDC9F54)stackoverflow.com](https://stackoverflow.com/questions/21080368/put-output-of-command-prompt-to-clipboard)

command output 

#### **8. Add the New User to the New Group**

Bash

```
sudo adduser name_user evaluating
```

Use code [with caution.](/faq#coding)

 [![Image of command outputs](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRfKKuEz3q2nHPiitGUaxOflpEUtfjYfxvdQvIJI6Pl95gd48b1DyTkLQAw6wmb) Opens in a new window](https://helpdeskgeek.com/how-to/redirect-output-from-command-line-to-text-file/) [![](https://encrypted-tbn2.gstatic.com/favicon-tbn?q=tbn:ANd9GcTwDV1r35OPqe9h4CZmUnnZJC1KxTvdBdbZUJp0n3Jh4CVuId4IHd4jL632ZuROVk2lUPVT8nvvLnZNAzDhLgvK33NfUkaFwtJGzg)helpdeskgeek.com](https://helpdeskgeek.com/how-to/redirect-output-from-command-line-to-text-file/)

command outputs 

#### **9. Verify Hostname is Correctly Set to login42**

 [![Image of command output](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSMsgqlK5alhmrJmvsGT0f3z-K76qV6qbKxas3864mtr7M4TiUvxrOVdYmpVpgs) Opens in a new window](https://superuser.com/questions/624385/how-do-i-capture-the-command-line-output-of-an-already-running-application) [![](https://encrypted-tbn0.gstatic.com/favicon-tbn?q=tbn:ANd9GcRjwenL3qwZRj6UKm-ix1TPs8PcGp4KSfaHtn7TcxsgbjMhCz5bEOMycznekNkLSseRQE8t1N4QFuVB4l5pEKQZRNJsVNZZkw)superuser.com](https://superuser.com/questions/624385/how-do-i-capture-the-command-line-output-of-an-already-running-application)

command output 

#### **10. Modify Hostname to Replace Your Login with Evaluator's (e.g., student42)**

Edit `/etc/hostname` and `/etc/hosts` to replace your login with `student42`. Restart the machine.

 [![Image of command output](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRSiogm9-fnkxhaat4AzPZTEHecNRuKbHNHBh4AwIA_qu5c8UreSM6zVefpvVyR) Opens in a new window](https://stackoverflow.com/questions/24701861/capturing-command-line-output-using-java) [![](https://encrypted-tbn0.gstatic.com/favicon-tbn?q=tbn:ANd9GcSZCmAD8gauBz6zQWhiwNyTdW_qTaFn86kY4i9ue0TKLdig0zZecaQOGXjB62-l1zYTQFINdpkKZYc51ilBK8hviR3QOYWdHDC9F54)stackoverflow.com](https://stackoverflow.com/questions/24701861/capturing-command-line-output-using-java)

command output 
