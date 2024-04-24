
5. **ft_itoa**
    - Prototype: `char *ft_itoa(int n);`
    - Parameters:
        - `n`: The integer to convert to a string.
    - Return value: The string representation of the integer 'n'. NULL if the allocation fails.
    - Description: Allocates (with malloc(3)) and returns a string representing the integer 'n'.
    - Example:
    ```c
    char *str = ft_itoa(12345);
    printf("%s\n", str);  // Outputs: "12345"
    free(str);
    ```

