NAME
     ft_strlcpy, ft_strlcat – size-bounded string copying and concatenation


SYNOPSIS
     #include <string.h>

     size_t
     ft_strlcpy(char * restrict dst, const char * restrict src, size_t dstsize);

     size_t
     ft_strlcat(char * restrict dst, const char * restrict src, size_t dstsize);

DESCRIPTION
     The ft_strlcpy() and ft_strlcat() functions copy and concatenate strings with the same input parameters and
     output result as snprintf(3).  They are designed to be safer, more consistent, and less error prone
     replacements for the easily misused functions strncpy(3) and strncat(3).

     ft_strlcpy() and ft_strlcat() take the full size of the destination buffer and guarantee NUL-termination if
     there is room.  Note that room for the NUL should be included in dstsize.  Also note that ft_strlcpy() and
     ft_strlcat() only operate on true ''C'' strings. This means that for ft_strlcpy() src must be NUL-terminated and
     for ft_strlcat() both src and dst() must be NUL-terminated.

     ft_strlcpy() copies up to dstsize - 1 characters from the string src to dst, NUL-terminating the result if
     dstsize is not 0.

     ft_strlcat() appends string src to the end of dst.  It will append at most dstsize - strlen(dst) - 1
     characters.  It will then NUL-terminate, unless dstsize is 0 or the original dst string was longer than
     dstsize (in practice this should not happen as it means that either dstsize is incorrect or that dst is
     not a proper string).

     If the src and dst strings overlap, the behavior is undefined.

RETURN VALUES
     Besides quibbles over the return type (size_t versus int) and signal handler safety (snprintf(3) is not
     entirely safe on some systems), the following two are equivalent:

           n = ft_strlcpy(dst, src, len);
           n = snprintf(dst, len, "%s", src);