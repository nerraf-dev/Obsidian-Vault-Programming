
To obtain the signature, the first thing we must do is shut down the virtual machine, since once you turn it on or modify something, the signature will change.

The next step will be to locate ourselves in the path where we have the .vdi of our virtual machine.

Finally, we will run `shasum machinename.vdi` and this will give us the signature. The result of this signature is what we will need to add to our signature.txt file and subsequently upload the file to the intra repository. It is very important not to reopen the machine since the signature will be modified. For corrections, remember to clone the machine so you can turn it on without fear of changing the signature.

**What is shasum?** It is a command that allows you to identify the integrity of a file using the SHA-1 hash check sum of a file.

