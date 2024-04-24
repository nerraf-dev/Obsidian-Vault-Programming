NAME
     ft_memmove – copy byte string

SYNOPSIS

     void *ft_memmove(void *dst, const void *src, size_t len);

DESCRIPTION
     The` ft_memmove()` function copies `len` bytes from string `src` to string `dst`.  The two strings may overlap; the copy is always done in a non-destructive manner.

RETURN VALUES
     The `ft_memmove()` function returns the original value of `dst`.

___
The provided code is a C implementation of the `memmove` function, which is a part of the standard C library. This function is used to copy a block of memory from a source address to a destination address, even if these memory regions overlap. The function is defined in a file named [``ft_memmove.c``](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FLibrary%2FCloudStorage%2FGoogleDrive-geeky.teacher.cs%40gmail.com%2FMy%20Drive%2FCampus42%2FProjects%2Flibft%2Flibft%2Fft_memmove.c%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/simon/Library/CloudStorage/GoogleDrive-geeky.teacher.cs@gmail.com/My Drive/Campus42/Projects/libft/libft/ft_memmove.c").

The function `ft_memmove` takes three parameters: `dest`, `src`, and `n`. `dest` is the destination address where the memory will be copied to. `src` is the source address from where the memory will be copied. `n` is the number of bytes to be copied.

Inside the function, it first checks if both `dest` and `src` are `NULL`. If they are, it returns `NULL` immediately. This is a safety check to prevent null pointer dereferencing.

Then, it casts `dest` and `src` to `unsigned char` pointers. This is done because memory operations in C are often performed on `unsigned char` pointers, which allows for byte-by-byte manipulation of the memory.

The function then checks if the destination address is greater than the source address. If it is, it means that the memory regions overlap in such a way that the beginning of the destination is in the middle of the source. In this case, it copies the bytes from the end of the source to the end of the destination, decrementing the index with each iteration. This is done to prevent overwriting the source data before it is copied.

If the destination address is not greater than the source address, it means that either the memory regions do not overlap, or they overlap in such a way that the beginning of the source is in the middle of the destination. In this case, it copies the bytes from the beginning of the source to the beginning of the destination, incrementing the index with each iteration. This is done to prevent overwriting the source data before it is copied.

Finally, the function returns a pointer to the destination address. This allows for function chaining, where the result of one function can be directly used as the input to another function.



```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   ft_memmove.c                                       :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/04/17 22:37:31 by sfarren           #+#    #+#             */
/*   Updated: 2024/04/18 17:33:43 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#include "libft.h"
/**
 * Copies a block of memory from a source address to a destination address,
 * handling overlapping memory regions correctly.
 *
 * @param dest The destination address where the memory will be copied to.
 * @param src The source address from where the memory will be copied.
 * @param n The number of bytes to be copied.
 * @return A pointer to the destination address.
 * 
 * The function takes three parameters: `dest` (the destination memory area),
 * `src` (the source memory area), and `n` (the number of bytes to copy). It
 * returns a pointer to the destination memory area.
 */
void	*ft_memmove(void *dest, const void *src, size_t n)
{
	size_t			i;
	unsigned char	*d;
	unsigned char	*s;

	/*
	* Check if both `dest` and `src` are `NULL`. 
	* If they are, it returns `NULL` immediately. This is a safety check to 
	* prevent null pointer dereferencing.
	*/
	if (!dest && !src)
		return (NULL);
	/*
	* casts `dest` and `src` to `unsigned char` pointers. This is done 
	* because with memory operations it allows for byte-by-byte manipulation of 
	* the memory.
	*/
	s = (unsigned char *)src;
	d = (unsigned char *)dest;
	i = 0;
	/*
	* Check if the destination address is greater than the source address. 
	* If it is, the memory regions overlap in such a way that the beginning of 
	* the destination is in the middle of the source. 
	*/
	if (d > s)
	{
	/*
	* it copies the bytes from the end of the source to the end of the 
	* destination, decrementing the index with each iteration. 
	* This is done to prevent overwriting the source data before it is copied.
	*/
		while (n-- > 0)
			d[n] = s[n];
	}
	/* 
	* If the destination address is not greater than the source address:
	* either the memory regions do not overlap, or they overlap in such a way 
	* that the beginning of the source is in the middle of the destination. 
	* In this case, it copies the bytes from the beginning of the source to the 
	* beginning of the destination
	*/
	else
	{
		while (i < n)
		{
			d[i] = s[i];
			i++;
		}
	}
	//returns a pointer to the destination address. 
	return (dest);
}


```


