1 ◦ If we want to connect via SSH we must close the machine and go to settings.
![[ssh-setting-the-network.png]]

2 ◦ Once there we will click on `Network`, click on `Advanced` so it shows more options, then we click on `Port fowarding`.
![[network-settings.png]]
3 ◦ Click on the emoji for adding a new rule.
![[add-port-forward.png]]
4 ◦ Lastly we will add the `4242` port to host and client. The IP's are not required. We will click accept so changes can be saved.

![[set-port-4242-vb.png]]

➤ To connect via ssh from the machine to the virtual machine using and the use the command `ssh <user>@localhost -p 4242`; it will ask for the password of the user that we are trying to log in. Once the password is introduced it will show or login in green, that will mean that the connections has been successfully.

[[10 - The Script]] -- >>
