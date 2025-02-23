
Uses libft.

## Makefile:

The `UNAME_S` variable captures the operating system name using the `uname -s` command. Depending on whether the system is macOS (`Darwin`) or Linux, it sets the CC variable to use either `gcc` or `clang` as the compiler, respectively. The `CFLAGS` variable is set to include common compiler flags: -`Wall` for all warnings, `-Wextra` for extra warnings, and `-Werror `to treat warnings as errors.

The `NAME` variable defines the output executable's name as `push_swap`. The `LIBFT_DIR` and `LIBFT` variables specify the directory and the static library file for the `libft` library, respectively.

The `SRCS` variable lists all the source files required for the project, organizsd by their respective directories. The `OBJS` variable converts these source file paths from `.c` to `.o` object files.

The all target depends on the `$(LIBFT)` and `$(NAME)` targets. The `$(LIBFT)` target changes the directory to `$(LIBFT_DIR)` and runs `make` to build the libft` `library. The `$(NAME)` target compiles the object files and links them with the `libft` library to create the final executable.

The pattern rule `%.o: %.c `specifies how to compile` .c` files into `.o` object files using the compiler and flags defined earlier.

The `clean` target removes the object files and also cleans the `libft` directory by invoking `make clean` in that directory. The `fclean` target extends clean by also removing the final executable and performing a full clean in the `libft` directory with `make fclean`. The `re` target forces a complete rebuild by invoking `fclean` followed by `all`.

Finally, the `.PHONY` directive declares the `all`, `clean`, `fclean`, and `re` targets as `phony`, meaning they do not correspond to actual files and should always be executed when invoked.

---
## push_swap.c

The main entry point to the program.
Contains the `isSorted`, `handle_error` and `main` functions. 

### `isSorted`:
The functions checks if an array of values is already in order. It simply iterates through the array comparing each element to the next. If the element being compared is greater than the next the function returns false to indicate the list is unsorted. 

### `handle_error`:
A utility function to output the error messages. It takes an error message, a split array of strings, and an integer array as arguments. It prints the error message using `ft_printf`, frees the memory allocated for the split array and the integer array if they are not `NULL`, and then exits the program with a status of 1.

## main
The main function creates an arrary of integers (`int_array`) after parsing the the arguments. 
If the the array is 5 numbers or less then `sort_Small` is called, otherwise `sort_big`.

