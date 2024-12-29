
```

      ERROR TEST
      NUMBER 3
      < input fizzBuzz | ls -la src/ > output


 - Bash output file:
total 36
drwxr-xr-x 2 simon simon 4096 Dec 29 16:34 .
drwxr-xr-x 7 simon simon 4096 Dec 29 17:30 ..
-rw-r--r-- 1 simon simon 4657 Dec 29 16:34 main.c
-rw-r--r-- 1 simon simon  833 Dec 29 16:34 runTest.c
-rw-r--r-- 1 simon simon 8492 Dec 29 16:34 test.c
-rw-r--r-- 1 simon simon  427 Dec 29 16:34 utils.c
\EOF

 - Pipex output file:
total 36
drwxr-xr-x 2 simon simon 4096 Dec 29 16:34 .
drwxr-xr-x 7 simon simon 4096 Dec 29 17:30 ..
-rw-r--r-- 1 simon simon 4657 Dec 29 16:34 main.c
-rw-r--r-- 1 simon simon  833 Dec 29 16:34 runTest.c
-rw-r--r-- 1 simon simon 8492 Dec 29 16:34 test.c
-rw-r--r-- 1 simon simon  427 Dec 29 16:34 utils.c
\EOF

 - Bash standard stream:
pipex: line 1: fizzBuzz: command not found
\EOF

 - Pipex standard stream:
/bin/sh: 1: fizzBuzz: not found
\EOF

 - Bash exit code value: 0

 - Pipex exit code value: 0

File permissions of output files match
```

The problem seems to be with the standard stream not matching. 