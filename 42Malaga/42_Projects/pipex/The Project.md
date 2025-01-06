# `pipex` Project Documentation

| **Program Name**       | **`pipex`**                                                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Turn-in Files**      | `Makefile, *.h, *.c`                                                                                                           |
| **Makefile Rules**     | `NAME, all, clean, fclean, re, bonus`                                                                                          |
| **Arguments**          | `file1 cmd1 cmd2 file2`                                                                                                        |
| **External Functions** | `open, close, read, write, malloc, free, perror, strerror, access, dup, dup2, execve, exit, fork, pipe, unlink, wait, waitpid` |
| **Libft Authorized**   | `Yes`                                                                                                                          |
| **Description**        | Recreate the behavior of a shell pipeline: `< file1 cmd1                                                                       |

---

## 1. Program Overview

The goal of `pipex` is to simulate the behaviour of a UNIX shell pipeline by redirecting input and output streams across commands. Your program will execute as:

```bash
./pipex file1 cmd1 cmd2 file2
```

### Arguments:

1. **`file1`**: Input file name.
2. **`cmd1`**, **`cmd2`**: Shell commands (with parameters).
3. **`file2`**: Output file name.

It must behave identically to the following shell command:

```bash
< file1 cmd1 | cmd2 > file2
```

---

## 2. Mandatory Features

Your program must meet the following criteria:

1. **Pipeline Functionality**:
    
    - Execute two shell commands in sequence (`cmd1` and `cmd2`), redirecting input and output appropriately.
2. **Error Handling**:
    
    - Handle errors as the shell would (e.g., invalid files or commands).
    - Prevent crashes caused by segmentation faults, double frees, or memory leaks.
3. **File Requirements**:
    
    - Submit a `Makefile`, `.h` header files, and `.c` source files.
    - Your `Makefile` must:
        - Compile with `cc` using `-Wall -Wextra -Werror` flags.
        - Include rules: `NAME`, `all`, `clean`, `fclean`, `re`.
        - Avoid unnecessary relinking.
4. **Memory Management**:
    
    - Properly free all allocated memory.
    - Ensure there are no memory leaks.
5. **Allowed Functions**:
    
    - You may use the following system functions:  
        `open`, `close`, `read`, `write`, `malloc`, `free`, `perror`, `strerror`, `access`, `dup`, `dup2`, `execve`, `exit`, `fork`, `pipe`, `unlink`, `wait`, `waitpid`.

---

## 3. Bonus Features

To go beyond the mandatory requirements, implement the following:

1. **Multiple Commands**:  
    Handle pipelines with more than two commands:
    
    ```bash
    ./pipex file1 cmd1 cmd2 cmd3 ... cmdn file2
    ```
    
    Equivalent to:
    
    ```bash
    < file1 cmd1 | cmd2 | cmd3 ... | cmdn > file2
    ```
    
2. **Here Document**:  
    Support "here_doc" functionality for input redirection:
    
    ```bash
    ./pipex here_doc LIMITER cmd cmd1 file
    ```
    
    Equivalent to:
    
```bash
    cmd << LIMITER | cmd1 >> file
```
    

> **Note**: Bonus features will only be evaluated if the mandatory part is implemented perfectly.

---

## 4. Development Guidelines

1. **Norm Compliance**:
    
    - Your project must adhere to the 42 Norm standard.
    - This applies to both mandatory and bonus files. Any violation will result in a score of 0.
2. **Testing**:
    
    - Create test programs to validate functionality. Although not graded, these will be invaluable during peer reviews and evaluations.
3. **Libft**:
    
    - If allowed, include your `libft` in a `libft/` directory.
    - Your `Makefile` must compile it before building your project.
4. **Submission**:
    
    - Work must be pushed to your assigned Git repository. Only files in the repository will be graded.

---

## 5. Additional Notes

- **Error Handling**: Handle errors such as invalid files, failed commands, or insufficient permissions as the shell does.
- **Memory Management**: Ensure all dynamically allocated memory is freed properly.

---

