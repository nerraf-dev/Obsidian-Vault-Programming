
The **calloc**() function allocates memory for an array of _nmemb_ elements of _size_ bytes each and returns a pointer to the allocated memory. The memory is set to zero. If _nmemb_ or _size_ is 0, then **calloc**() returns either NULL, or a unique pointer value that can later be successfully passed to **free**().


Need to know malloc() - 


SYNOPSIS
     #include <stdlib.h>

     void *
     calloc(size_t count, size_t size);
DESCRIPTION
     The malloc(), calloc(), valloc(), realloc(), and reallocf() functions allocate memory.  The allocated memory is aligned such that it can be used for any data type, including AltiVec- and SSE-related types.
     The aligned_alloc() function allocates memory with the requested alignment.  The free() function frees allocations that were created via the preceding allocation functions.
	
	The malloc() function allocates size bytes of memory and returns a pointer to the allocated memory.

     The calloc() function contiguously allocates enough space for count objects that are size bytes of memory each and returns a pointer to the allocated memory.  The allocated memory is filled with bytes of value zero.

     
  RETURN VALUES
     If successful, calloc(), malloc(), realloc(), reallocf(), valloc(), and aligned_alloc() functions return a pointer to allocated memory.  If there is an error, they return a NULL pointer and set errno to ENOMEM.

     In addition, aligned_alloc() returns a NULL pointer and sets errno to EINVAL if size is not an integral multiple of alignment, or if alignment is not a power of 2 at least as large as sizeof(void *).

     For realloc(), the input pointer is still valid if reallocation failed.  For reallocf(), the input pointer will have been freed if reallocation failed.

     The free() function does not return a value.

DEBUGGING ALLOCATION ERRORS
     A number of facilities are provided to aid in debugging allocation errors in applications.  These
     facilities are primarily controlled via environment variables.  The recognized environment variables and
     their meanings are documented below.



```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   ft_calloc.c                                        :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/04/18 11:19:38 by sfarren           #+#    #+#             */
/*   Updated: 2024/04/18 11:25:45 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#include "libft.h"
/*
The calloc() function allocates memory for an array of nmemb elements of 
size bytes each and returns a pointer to the allocated memory. The memory is
 set to zero. If nmemb or size is 0, then calloc() returns either NULL, or a
  unique pointer value that can later be successfully passed to free().
  */
void *ft_calloc(size_t nmemb, size_t size)
{
    void    *ptr;   // Pointer to the allocated memory

    // Allocate memory for nmemb elements of size bytes each
    ptr = malloc(nmemb * size);
    if (!ptr)   // If malloc fails, return NULL
        return (NULL);
    // Set the allocated memory to zero using existing bzero function
    ft_bzero(ptr, nmemb * size);
    return (ptr);
}
```

The errno is a global variable set by system calls and some library functions in the event of an error to indicate what went wrong. Its value is significant only when the return value of the call indicated an error (i.e., -1 from most system calls; a NULL pointer from most library functions); a function that succeeds is allowed to change errno.

In the case of calloc, if there's an error (like not enough memory available), it will return NULL and set errno to ENOMEM.

However, in your custom ft_calloc function, you're not setting errno to ENOMEM when malloc fails. This is because malloc itself will set errno to ENOMEM if it fails due to insufficient memory. So, in your custom function, you don't need to manually set errno to ENOMEM.