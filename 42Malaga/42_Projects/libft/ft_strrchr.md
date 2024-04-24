NAME
     ft_strchr, ft_strrchr – locate character in string

SYNOPSIS

     char *
     ft_strchr(const char *s, int c);

     char *
     ft_strrchr(const char *s, int c);

DESCRIPTION
     The `ft_strchr()` function locates the first occurrence of `c` (converted to a char) in the string pointed to by `s`.  The terminating `null` character is considered to be part of the string; therefore if c is ‘`\0’`, the functions locate the terminating ‘`\0’`.

	The ft_strrchr() function is identical to ft_strchr(), except it locates the last occurrence of c.

RETURN VALUES
     The functions ft_strchr() and ft_strrchr() return a pointer to the located character, or NULL if the character does not appear in the string.