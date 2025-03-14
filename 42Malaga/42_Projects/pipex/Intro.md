
| **Program name**     | **`pipex`**                                                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Turn in files**    | `Makefile, *.h, *.c`                                                                                                           |
| **Makefile**         | `NAME, all, clean, fclean, re`                                                                                                 |
| **Arguments**        | `file1 cmd1 cmd2 file2`                                                                                                        |
| **External functs.** | `open, close, read, write, malloc, free, perror, strerror, access, dup, dup2, execve, exit, fork, pipe, unlink, wait, waitpid` |
| **Libft authorized** | `Yes`                                                                                                                          |
| **Description**      | `This project is about handling pipes.`                                                                                        |
|                      |                                                                                                                                |

Your program will be executed as follows:

```
./pipex file1 cmd1 cmd2 file2
```

It must take 4 arguments:  
• `file1` and `file2` are file names.

• `cmd1` and `cmd2` are shell commands with their parameters.

It must behave exactly the same as the shell command below:

```bash
$> < file1 cmd1 | cmd2 > file2
```


## Requirements

Your project must comply with the following rules:
- You have to turn in a `Makefile` which will compile your source files. It must not relink.
- You have to handle errors thoroughly. In no way your program should quit unexpectedly (segmentation fault, bus error, double free, and so forth).
- Your program mustn’t have memory leaks.
- If you have any doubt, handle the errors like the shell command:
	`< file1 cmd1 | cmd2 > file2`

## Common Instructions

- Your project must be written in C.
    
- Your project must be written in accordance with the Norm. If you have bonus files/functions, they are included in the norm check and you will receive a 0 if there is a norm error inside.
    
- Your functions should not quit unexpectedly (segmentation fault, bus error, double free, etc) apart from undefined behaviours. If this happens, your project will be considered non functional and will receive a 0 during the evaluation.
    
- All heap allocated memory space must be properly freed when necessary. No leaks will be tolerated.
    
- If the subject requires it, you must submit a Makefile which will compile your source files to the required output with the flags `-Wall`, `-Wextra` and `-Werror`, use `cc`, and your Makefile must not relink.
    
- Your Makefile must at least contain the rules `$(NAME)`, `all`, `clean`, `fclean` and `re`.
    
- To turn in bonuses to your project, you must include a rule bonus to your Makefile, which will add all the various headers, librairies or functions that are forbidden on the main part of the project. Bonuses must be in a different `file _bonus.{c/h}` if the subject does not specify anything else. Mandatory and bonus part evaluation is done separately.
    
- If your project allows you to use your libft, you must copy its sources and its associated Makefile in a libft folder with its associated Makefile. Your project’s Makefile must compile the library by using its Makefile, then compile the project.
    
- We encourage you to create test programs for your project even though this work won’t have to be submitted and won’t be graded. It will give you a chance to easily test your work and your peers’ work. You will find those tests especially useful during your defence. Indeed, during defence, you are free to use your tests and/or the tests of the peer you are evaluating.
    
- Submit your work to your assigned git repository. Only the work in the git repository will be graded. If Deepthought is assigned to grade your work, it will be done