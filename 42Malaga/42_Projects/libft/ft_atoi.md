NAME
     atoi, atoi_l – convert ASCII string to integer

LIBRARY
     Standard C Library (libc, -lc)

     int
     atoi(const char *str);

    
DESCRIPTION
     The atoi() function converts the initial portion of the string pointed to by str to int
     representation.

     It is equivalent to:

           (int)strtol(str, (char **)NULL, 10);

     While the atoi() function uses the current locale

IMPLEMENTATION NOTES
     The atoi()  is thread-safe and async-cancel-safe.

     The strtol() and strtol_l() functions are recommended instead of atoi() and atoi_l() functions, especially in new code.


### Understandable explanation

The `atoi()` function converts a string to its `int` representation.

Some things that the `atoi()` function does are not clearly said in the man. I'll quickly list them here.

- The string passed as parameter may begin with an arbitrary number of whitespaces as determined by `isspace(3)`
    
- After the arbitrary number of whitespaces, there can be one single optional '+' or '-' sign
    
- The remainder of the string will be converted to an int, stopping at the first character which is not a valid digit in the given base (in our case we only need to manage base 10, so the valid digits are 0-9)


[[ft_atoi info]]