decimal-digit character test

     int ft_isdigit(int c);

DESCRIPTION
     The ft_isdigit() function tests for a decimal digit character.  Regardless of locale, this includes the following characters only:

     ``0''``1''``2''``3''``4''
     ``5''``6''``7''``8''``9''
The value of the argument must be representable as an unsigned char or the value of EOF.

RETURN VALUES
     returns zero if the character tests false and return non-zero if the character tests true.
     
```c
int	ft_isdigit(int c)
{
	if (c >= '0' && c <= '9')
		return (c);
	else
		return (0);
}
```