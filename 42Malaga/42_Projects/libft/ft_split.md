**ft_split**
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

