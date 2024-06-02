# ft_atoi

Convert an ASCII string to integer

## PROTOTYPE
int ft_atoi(const char *str);

    
## DESCRIPTION
The ft_atoi() function converts the initial portion of the string pointed to by str to int representation.

## IMPLEMENTATION NOTES
The ft_ atoi()  is thread-safe and async-cancel-safe.

### UNDERSTANDABLE EXPLANATION

The `atoi()` function converts a string to its `int` representation.

Some things that the `atoi()` function does are not clearly said in the man. I'll quickly list them here.

- The string passed as parameter may begin with an arbitrary number of whitespaces as determined by `isspace(3)`
- After the arbitrary number of whitespaces, there can be one single optional '+' or '-' sign
- The remainder of the string will be converted to an int, stopping at the first character which is not a valid digit in the given base (in our case we only need to manage base 10, so the valid digits are 0-9)

<details>
<summary>Annotated ft_atoi.c</summary>

```c
     //the code here
```
[[ft_atoi info]]

</details>