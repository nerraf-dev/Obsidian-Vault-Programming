Here are the details of the functions extracted from the document:

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

4. **ft_split**
    - Prototype: `char **ft_split(char const *s, char c);`
    - Parameters:
        - `s`: The string to split.
        - `c`: The delimiter character.
    - Return value: An array of strings resulting from the split. NULL if the allocation fails.
    - Description: Allocates (with malloc(3)) and returns an array of strings obtained by splitting 's' using the character 'c' as a delimiter.
    - Example:
    ```c
    char **result = ft_split("apple,banana,cherry", ',');
    // result[0] = "apple", result[1] = "banana", result[2] = "cherry"
    free(result);
    ```

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

