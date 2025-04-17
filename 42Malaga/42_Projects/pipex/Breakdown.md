
### **Overview**
The program implements a pipeline-like behaviour, where two commands (`cmd1` and `cmd2`) are executed in sequence, with the output of the first command being passed as input to the second command. The program takes four arguments:
1. `file1`: Input file for the first command.
2. `cmd1`: The first command to execute.
3. `cmd2`: The second command to execute.
4. `file2`: Output file for the second command.

The program uses pipes (`pipefd`), `fork()` to create child processes, and `execve()` (likely in `child_handler` and `parent_handler`) to execute the commands.

---

### **Key Functions**

#### **`arg_error()`**
This function handles invalid arguments. If the number of arguments is incorrect, it prints an error message and exits the program.

```c
static void	arg_error(void)
{
	ft_printf_fd(2, "Error: Bad arguments\n");
	ft_printf_fd(2, "Usage: %s file1 cmd1 cmd2 file2\n", "pipex");
	exit(EXIT_FAILURE);
}
```

---

#### **`push_swap()`**
This is the core function that:
1. Validates the argument count.
2. Creates a pipe for inter-process communication.
3. Forks two child processes:
   - **Child 1**: Handles the first command (`cmd1`).
   - **Child 2**: Handles the second command (`cmd2`).
4. Waits for both child processes to finish and returns the exit status of the second command.

Key steps:
- **Pipe Creation**: `create_pipe(pipefd)` initializes a pipe.
- **Forking**: `fork_child()` creates child processes.
- **Child 1**: Writes the output of `cmd1` to the pipe.
- **Child 2**: Reads from the pipe and writes the output of `cmd2` to `file2`.
- **Closing Pipes**: Ensures proper cleanup of file descriptors.
- **Waiting**: `waitpid()` waits for child processes to finish.

---

#### **`main()`**
The entry point of the program:
1. Validates the argument count.
2. Calls `push_swap()` to execute the pipeline logic.

```c
int	main(int argc, char **argv, char **envp)
{
	if (argc < 5)
		arg_error();
	return (push_swap(argc, argv, envp));
}
```

---

### **How It Works**
1. **Input Validation**: Ensures the correct number of arguments.
2. **Pipe Setup**: Creates a unidirectional communication channel.
3. **Child Processes**:
   - The first child executes `cmd1` and writes its output to the pipe.
   - The second child reads from the pipe and executes `cmd2`, writing its output to `file2`.
4. **Synchronization**: The parent process waits for both children to finish.
5. **Exit Status**: Returns the exit status of the second command.

---

### **Potential Improvements**
1. **Error Handling**: Add error checks for system calls like `pipe()`, `fork()`, and `waitpid()`.
2. **Modularity**: Break down `push_swap()` into smaller functions for better readability.
3. **Resource Management**: Ensure all file descriptors are properly closed in case of errors.


---

### **What is Process Management?**
Process management involves creating, running, synchronizing, and terminating processes. A process is an instance of a program in execution, and the operating system is responsible for managing these processes to ensure efficient use of system resources.

In your code, process management is achieved using system calls like `fork()`, `waitpid()`, and `execve()` (likely in `child_handler` and `parent_handler`).

---

### **Key Concepts in Process Management**

#### **1. Process Creation**
- **`fork()`**: This system call creates a new process by duplicating the current process (parent). The new process (child) gets its own memory space and process ID.
  - In your code:
    ```c
    pid[0] = fork_child();
    pid[1] = fork_child();
    ```
    Two child processes are created. Each child inherits the parent's code and starts executing from the point where `fork()` was called.

- **Parent vs. Child**:
  - The return value of `fork()` determines the process:
    - `0`: Indicates the child process.
    - Positive value: Indicates the parent process, with the return value being the child's PID.

---

#### **2. Inter-Process Communication (IPC)**
- **Pipes**: Pipes (`pipefd`) are used to allow processes to communicate. One process writes to the pipe, and another reads from it.
  - In your code:
    ```c
    create_pipe(pipefd);
    ```
    A pipe is created, and the file descriptors (`pipefd[0]` for reading, `pipefd[1]` for writing) are passed to the child processes.

---

#### **3. Process Execution**
- **`execve()`**: This system call replaces the current process image with a new one, effectively running a new program. It's likely used in `child_handler` and `parent_handler` to execute the commands (`cmd1` and `cmd2`).
  - Example:
    ```c
    execve("/bin/ls", args, envp);
    ```
    This replaces the current process with the `ls` command.

---

#### **4. Process Synchronization**
- **`waitpid()`**: The parent process waits for child processes to finish execution. This ensures the parent doesn't terminate before its children.
  - In your code:
    ```c
    waitpid(pid[0], &status[0], 0);
    waitpid(pid[1], &status[1], 0);
    ```
    The parent waits for both child processes to complete.

- **Exit Status**: The macro `WIFEXITED(status)` checks if a child exited normally, and `WEXITSTATUS(status)` retrieves its exit code.

---

#### **5. Process Termination**
- **`exit()`**: A process can terminate itself using `exit()`. In your code, this happens in `arg_error()` if the arguments are invalid.

---

### **How It Works in Your Code**
1. **Parent Process**:
   - Creates a pipe.
   - Forks two child processes.
   - Waits for both children to finish.
   - Returns the exit status of the second child.

2. **Child Processes**:
   - The first child writes the output of `cmd1` to the pipe.
   - The second child reads from the pipe and executes `cmd2`.

3. **Synchronization**:
   - The parent ensures both children complete before exiting.

---

### **Why Process Management Matters**
- **Concurrency**: Allows multiple tasks to run simultaneously.
- **Resource Sharing**: Enables processes to share data (e.g., via pipes).
- **Efficiency**: Ensures proper use of CPU and memory.

Let me know if you'd like a deeper dive into any specific part!