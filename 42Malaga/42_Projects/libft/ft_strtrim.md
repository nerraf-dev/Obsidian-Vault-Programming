
3. **ft_strtrim**
    - Prototype: `char *ft_strtrim(char const *s1, char const *set);`
    - Parameters:
        - `s1`: The string to trim.
        - `set`: The set of characters to trim from the beginning and end of 's1'.
    - Return value: The trimmed string. NULL if the allocation fails.
    - Description: Allocates (with malloc(3)) and returns a copy of 's1' with the specified set of characters removed from the beginning and end.
    - Example:
    ```c
    char *str = ft_strtrim("   Hello, World!   ", " ");
    printf("%s\n", str);  // Outputs: "Hello, World!"
    free(str);
    ```

