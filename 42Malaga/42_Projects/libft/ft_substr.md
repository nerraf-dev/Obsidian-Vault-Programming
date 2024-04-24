1. **ft_substr**
    - Prototype: `char *ft_substr(char const *s, unsigned int start, size_t len);`
    - Parameters:
        - `s`: The string from which to create the substring.
        - `start`: The start index of the substring in the string 's'.
        - `len`: The maximum length of the substring.
    - Return value: The substring. NULL if the allocation fails.
    - Description: Allocates (with malloc(3)) and returns a substring from the string 's'. The substring begins at index 'start' and is of maximum size 'len'.
    - Example:
    ```c
    char *str = ft_substr("Hello, World!", 7, 5);
    printf("%s\n", str);  // Outputs: "World"
    free(str);
    ```
