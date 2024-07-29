get_next_line.c
```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   get_next_line.c                                    :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/07/27 17:48:24 by sfarren           #+#    #+#             */
/*   Updated: 2024/07/27 20:42:43 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#include "get_next_line.h"

/**
 * Finds the position of the first occurrence of a
 * newline character ('\n') in a string.
 *
 * @param str The string to search for a newline character.
 * @return The position of the first newline character in
 *   the string, or 0 if not found.
 */
int	ft_find_nl(const char *str)
{
	int	i;

	i = 0;
	if (!str)
		return (0);
	while (str[i])
	{
		if (str[i] == '\n')
			return (++i);
		i++;
	}
	return (0);
}

/**
* Frees the buffer allocated by malloc
* Sets the pointer to null
**/
char	*ft_free_buf(char **str)
{
	free(*str);
	*str = NULL;
	return (NULL);
}

char	*ft_result_buf(char **buf)
{
	char	*temp;
	char	*result_buf;
	int		nl_loc;

	temp = ft_strdup(*buf);
	ft_free_buf(buf);
	if (!temp)
		return (NULL);
	if (!ft_find_nl(temp))
	{
		result_buf = ft_strdup(temp);
		ft_free_buf(&temp);
		return (result_buf);
	}
	nl_loc = ft_find_nl(temp);
	result_buf = ft_substr(temp, 0, nl_loc);
	if (!result_buf)
		return (ft_free_buf(&temp));
	*buf = ft_substr(temp, nl_loc, ft_strlen(temp) - nl_loc);
	ft_free_buf(&temp);
	if (!*buf || !*buf[0])
		ft_free_buf(buf);
	return (result_buf);
}

char	*ft_new_buffer(char *buf, int fd)
{
	char	*new_buf;
	int		bytes_read;

	bytes_read = 1;
	new_buf = (char *)malloc(BUFFER_SIZE + 1);
	if (!new_buf)
		return (NULL);
	while (bytes_read > 0 && !ft_find_nl(buf))
	{
		bytes_read = read(fd, new_buf, BUFFER_SIZE);
		if (bytes_read == -1)
		{
			ft_free_buf(&new_buf);
			return (ft_free_buf(&buf));
		}
		new_buf[bytes_read] = '\0';
		if (!buf && bytes_read > 0)
			buf = ft_strdup(new_buf);
		else if (bytes_read > 0)
			buf = ft_strjoin(buf, new_buf);
	}
	ft_free_buf(&new_buf);
	return (buf);
}

char	*get_next_line(int fd)
{
	static char	*buf;

	if (fd < 0 || BUFFER_SIZE <= 0)
		return (NULL);
	if (!buf || !ft_find_nl(buf))
		buf = ft_new_buffer(buf, fd);
	if (!buf)
		return (NULL);
	return (ft_result_buf(&buf));
}
```

get_next_line_utils.c
```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   get_next_line_utils.c                              :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/07/27 17:48:33 by sfarren           #+#    #+#             */
/*   Updated: 2024/07/27 20:43:21 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#include "get_next_line.h"

size_t	ft_strlen(const char *str)
{
	size_t	i;

	i = 0;
	while (str[i] != '\0')
		i++;
	return (i);
}

char	*ft_strdup(const char *str)
{
	char	*str_copy;
	size_t	len;

	len = ft_strlen(str);
	str_copy = (char *)malloc(len +1);
	if (!str_copy)
		return (NULL);
	ft_memcpy(str_copy, str, len);
	str_copy[len] = '\0';
	return (str_copy);
}

char	*ft_substr(char const *s, unsigned int start, size_t len)
{
	char	*substr;
	size_t	i;
	size_t	j;

	if (!s)
		return (0);
	if (start > ft_strlen(s))
		return (ft_strdup(""));
	if (start + len > ft_strlen(s))
		len = ft_strlen(s) - start;
	substr = ft_calloc(len + 1, 1);
	if (!substr)
		return (0);
	i = 0;
	j = start;
	while (i < len)
	{
		substr[i] = s[j];
		i++;
		j++;
	}
	return (substr);
}
```
