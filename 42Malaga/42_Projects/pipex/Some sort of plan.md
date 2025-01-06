The basic idea to cover the mandatory section is as follows:

- Define variables
- Perform initial checks
	- check environment is present/not null, this holds the `PATH` value
	- check the number of arguments
- If there are 5 arguments:
	- Create a pipe 
	- Create a fork
		- The child process
			- will handle the input file opening/presence
			- duplicate the `fd` of the input file over the `STDIN` to become input for the command
			- duplicate the pipe **write** end over STDOUT to capture cmd output.
			- close the input file
			- execute the command
				- Execute!
		- The parent process
			-  handle the output file
			- duplicate the read end of the pipe over STDIN
			- duplicate the output file fd over STDOUT
			- close open unused fds (can fd)
			- execute command!
				- Execute!

Executing the command:
The commands will be 'strings' within the `argv` array., e.g. "wc -l". We need to be able to tell is we can run the command, or if it even exists. So we need to separate any arguments from the command. 

* split the cmd from arguments and store
* Get the path and check access to the command
* execute the command and return errors if needed. 

Clean up


Create Wrappers for:
* pipe
* fork
* dup2

Functions for error handling


```c
int	main(int argc, char **argv, char **envp)
{
	int		pipefd[2];
	pid_t	pid1;

	if (envp == NULL || envp[0] == NULL)
		envp = NULL;
	if (argc == 5)
	{
		// Create a pipe - pipefd[0] is for reading, pipefd[1] is for writing
		create_pipe(pipefd);    // A wrapper for pipe 
		pid1 = fork_child();   // wrapper for fork
		if (pid1 == 0)
			child_handler(pipefd, argv, envp);  // Handler function
		waitpid(pid1, NULL, 0);
		parent_handler(pipefd, argv, envp);    // Handler function
	}
	// Error if not 5 arguments
	else
	{
		ft_printf_fd(2, "\033[31mError: Bad arguments\n\e[0m");
		ft_printf_fd(2,"Usage: %s file1 cmd1 cmd2 file2\n", argv[0]);
	}
	close(pipefd[0]);
	close(pipefd[1]);
	return (0);
}
```