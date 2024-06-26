NAME
     ft_memcpy – copy memory area

SYNOPSIS

     void *ft_memcpy(void *restrict dst, const void *restrict src, size_t n);

DESCRIPTION
     The `ft_memcpy() `function copies n bytes from memory area src to memory area `dst`.  If `dst` and src overlap, behavior is undefined.  Applications in which `dst` and `src` might overlap should use `memmove()` instead.

RETURN VALUES
     The ft_memcpy() function returns the original value of dst.