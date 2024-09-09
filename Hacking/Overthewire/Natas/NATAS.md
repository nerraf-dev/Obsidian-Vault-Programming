Natas teaches the basics of serverside web-security.

Each level of natas consists of its own website located at **http://natasX.natas.labs.overthewire.org**, where X is the level number. There is **no SSH login**. To access a level, enter the username for that level (e.g. natas0 for level 0) and its password.

Each level has access to the password of the next level. Your job is to somehow obtain that next password and level up. **All passwords are also stored in /etc/natas_webpass/**. E.g. the password for natas5 is stored in the file /etc/natas_webpass/natas5 and only readable by natas4 and natas5.

## Start here - Natas0

```
Username: natas0
Password: natas0
URL:      http://natas0.natas.labs.overthewire.org
```


![[natas0.png]]


> [!faq]- password 
>  `<!--The password for natas1 is 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq -->`


## Natas1

```
Username: natas1
Password: << from previous level >>
URL:      http://natas1.natas.labs.overthewire.org
```


![[natas1.png]]

> [!faq]- password 
>  `<!--The password for natas2 is TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI -->`


# Natas Level 1 → Level 2

```
Username: natas2
URL:      http://natas2.natas.labs.overthewire.org
```

![[natas2.png]]

How can you find the content?


Look at the source code, check the content

>[!faq]- Solution 
>Inside the content element, there is an image. The image itself is of no use...but it does indicate a directory.
>  `natas3:3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH`



# Natas Level 3 → Level 4

```
Username: natas4
URL:      http://natas4.natas.labs.overthewire.org
```

![[natas3-01.png]]

![[natas3-sol-html.png]]

Hint: `robots.txt`

```
User-agent: *
Disallow: /s3cr3t/
```

`natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`


# Natas Level 3 → Level 4

```
Username: natas4
URL:      http://natas4.natas.labs.overthewire.org
```

![[natas4.png]]



```
Access granted. The password for natas5 is 0n35PkggAPm2zbEpOU802c0x0Msn1ToK
```


# Natas Level 4 → Level 5

```
Username: natas5
URL:      http://natas5.natas.labs.overthewire.org
```

The page says you're not logged in. how does it know?


`Access granted. The password for natas6 is 0RoJwHdSKWFTYR5WuiAewauSuNaBXned`