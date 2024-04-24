     char *strnstr(const char *haystack, const char *needle, size_t len);


DESCRIPTION
     The `strnstr()` function locates the first occurrence of the null-terminated string **needle** in the string **haystack**, *where not more than* `len` *characters are searched*.  Characters that appear after a ‘`\0`’ character are not searched.  

 RETURN VALUES
     If needle is an empty string, haystack is returned; if needle occurs nowhere in haystack, NULL is returned; otherwise a pointer to the first character of the first occurrence of needle is returned.

EXAMPLES
     The following sets the pointer ptr to the "Bar Baz" portion of largestring:

           const char *largestring = "Foo Bar Baz";
           const char *smallstring = "Bar";
           char *ptr;

           ptr = strstr(largestring, smallstring);

   The following sets the pointer ptr to NULL, because only the first 4 characters of largestring are searched:

           const char *largestring = "Foo Bar Baz";
           const char *smallstring = "Bar";
           char *ptr;

           ptr = strnstr(largestring, smallstring, 4);