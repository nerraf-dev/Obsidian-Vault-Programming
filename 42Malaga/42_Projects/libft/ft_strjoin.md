

2. **ft_strjoin**
    - Prototype: `char *ft_strjoin(char const *s1, char const *s2);`
    - Parameters:
        - `s1`: The prefix string.
        - `s2`: The suffix string.
    - Return value: The new string. NULL if the allocation fails.
    - Description: Allocates (with malloc(3)) and returns a new string, which is the result of the concatenation of 's1' and 's2'.
    - Example:
    ```c
    char *str = ft_strjoin("Hello, ", "World!");
    printf("%s\n", str);  // Outputs: "Hello, World!"
    free(str);
    ```


