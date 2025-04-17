```
1. Process Creation
fork(): This system call creates a new process by duplicating the current process (parent). The new process (child) gets its own memory space and process ID.

In your code:
Two child processes are created. Each child inherits the parent's code and starts executing from the point where fork() was called.
Parent vs. Child:

The return value of fork() determines the process:
0: Indicates the child process.
Positive value: Indicates the parent process, with the return value being the child's PID.
```
I added some output to see the PID and got this, so how does this relate to the process. I call fork twice. So I assume that this is the 339921/2 values. 

pid[0] I assume is 339921 and this is the main/current process at present. When the child process is created this has a pid of 0 and as it begins execution from the fork call the if statement runs, closing the pipe read end (?) and handles the command.

Meanwhile The main process continues, creates another fork and the child process runs the code in the if statement whils the main process continues cloising the pipe and waiting for the other process to finish. 

Forked process with PID: 339921
Forked process with PID: 339922
Forked process with PID: 0
Forked process with PID: 0

---

---

### **How `fork()` Works in My Code**
1. **First `fork()` Call**:
   - The parent process (let's assume its PID is `339921`) calls `fork()`.
   - This creates a new child process (let's assume its PID is `339922`).
   - In the parent process, `fork()` returns the PID of the child (`339922`), so `pid[0]` is set to `339922`.
   - In the child process, `fork()` returns `0`, so the `if (pid[0] == 0)` block runs in the child process.

2. **Second `fork()` Call**:
   - The parent process (still PID `339921`) calls `fork()` again.
   - This creates another child process (let's assume its PID is `339923`).
   - In the parent process, `fork()` returns the PID of the second child (`339923`), so `pid[1]` is set to `339923`.
   - In the second child process, `fork()` returns `0`, so the `if (pid[1] == 0)` block runs in the second child process.

---

### **How the Processes Work Together**
1. **Parent Process (PID `339921`)**:
   - Creates the first child process (`339922`).
   - Continues execution after the first `fork()` and creates the second child process (`339923`).
   - Waits for both child processes to finish using `waitpid()`.

2. **First Child Process (PID `339922`)**:
   - Executes the `if (pid[0] == 0)` block.
   - Closes the read end of the pipe (`pipefd[0]`).
   - Executes `child_handler()` to handle the first command (`cmd1`).

3. **Second Child Process (PID `339923`)**:
   - Executes the `if (pid[1] == 0)` block.
   - Closes the write end of the pipe (`pipefd[1]`).
   - Executes `parent_handler()` to handle the second command (`cmd2`).

---

### **Key Points to Remember**
- **Parent Process**:
  - Continues execution after each `fork()` and manages the overall flow (e.g., creating pipes, waiting for children).
  - `pid[0]` and `pid[1]` store the PIDs of the first and second child processes, respectively.

- **Child Processes**:
  - Each child process starts executing from the point where `fork()` was called.
  - In the child processes, `fork()` returns `0`, so the `if (pid[0] == 0)` or `if (pid[1] == 0)` blocks are executed.

- **Pipe Management**:
  - The first child process closes the read end of the pipe (`pipefd[0]`) because it only writes to the pipe.
  - The second child process closes the write end of the pipe (`pipefd[1]`) because it only reads from the pipe.

---

### **Visual Representation**
Here’s a simplified flow of the processes:

```
Parent Process (PID 339921)
  ├── First Child Process (PID 339922)
  │     └── Executes `child_handler()` (handles cmd1)
  └── Second Child Process (PID 339923)
        └── Executes `parent_handler()` (handles cmd2)
```

---

