```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   get_next_line.c                                    :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/07/27 17:48:24 by sfarren           #+#    #+#             */
/*   Updated: 2024/07/29 13:04:25 by sfarren          ###   ########.fr       */
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

char	*gnl_free_buf(char **buf)
{
	free(*buf);
	*buf = NULL;
	return (NULL);
}

char	*gnl_new_buffer(char *buf, int fd)
{
	char	*new_buf;
	int		bytes_read;

	bytes_read = 1;
	new_buf = (char *)malloc(BUFFER_SIZE + 1);
	if (!new_buf)
		return (gnl_free_buf(&buf));
	while (bytes_read > 0 && !gnl_find_nl(buf))
	{
		bytes_read = read(fd, new_buf, BUFFER_SIZE);
		if (bytes_read < 0)
		{
			gnl_free_buf(&new_buf);
			return (gnl_free_buf(&buf));
		}
		new_buf[bytes_read] = '\0';
		if (!buf && bytes_read > 0)
			buf = gnl_strdup(new_buf);
		else if (bytes_read > 0)
			buf = gnl_str_join(buf, new_buf);
	}
	gnl_free_buf(&new_buf);
	return (buf);
}

char	*gnl_result_buf(char **buf)
{
	char	*temp;
	char	*result_buf;
	int		nl_loc;

	temp = gnl_strdup(*buf);
	gnl_free_buf(buf);
	if (!temp)
		return (gnl_free_buf(&temp));
	if (!gnl_find_nl(temp))
	{
		result_buf = gnl_strdup(temp);
		gnl_free_buf(&temp);
		return (result_buf);
	}
	nl_loc = gnl_find_nl(temp);
	result_buf = gnl_substr(temp, 0, nl_loc);
	if (!result_buf)
		return (gnl_free_buf(&temp));
	*buf = gnl_substr(temp, nl_loc, gnl_strlen(temp) - nl_loc);
	gnl_free_buf(&temp);
	if (!*buf || !*buf[0])
		gnl_free_buf(buf);
	return (result_buf);
}

char	*get_next_line(int fd)
{
	static char	*buf;

	if (fd < 0 || BUFFER_SIZE <= 0)
		return (NULL);
	if (!buf || !gnl_find_nl(buf))
		buf = gnl_new_buffer(buf, fd);
	if (!buf)
		return (NULL);
	return (gnl_result_buf(&buf));
}
```


```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   get_next_line_utils.c                              :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/07/27 17:48:33 by sfarren           #+#    #+#             */
/*   Updated: 2024/07/29 13:03:40 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#include "get_next_line.h"

size_t	gnl_strlen(const char *str)
{
	int	i;

	i = 0;
	while (str[i] != '\0')
		i++;
	return (i);
}

int	gnl_find_nl(const char *str)
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

char	*gnl_strdup(char *str)
{
	char	*str_copy;
	int		len;
	int		i;

	i = 0;
	len = gnl_strlen(str);
	str_copy = (char *)malloc(len +1);
	if (!str_copy)
		return (NULL);
	while (str[i])
	{
		str_copy[i] = str[i];
		i++;
	}
	str_copy[i] = '\0';
	return (str_copy);
}

char	*gnl_substr(char const *s, unsigned int start, size_t len)
{
	char	*substr;
	size_t	i;
	size_t	j;

	if (!s)
		return (0);
	if (start > gnl_strlen(s))
		return (gnl_strdup(""));
	if (start + len > gnl_strlen(s))
		len = gnl_strlen(s) - start;
	substr = (char *)malloc(len + 1);
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
	substr[i] = '\0';
	return (substr);
}

char	*gnl_str_join(char const *s1, char const *s2)
{
	size_t	s1_len;
	size_t	s2_len;
	size_t	i;
	char	*s3;

	s1_len = gnl_strlen(s1);
	s2_len = gnl_strlen(s2);
	s3 = (char *)malloc(s1_len + s2_len + 1);
	if (!s3)
		return (gnl_free_buf((char **)&s1));
	i = 0;
	while (i < s1_len)
	{
		s3[i] = s1[i];
		i++;
	}
	while (*s2)
	{
		s3[i] = *s2++;
		i++;
	}
	s3[i] = '\0';
	gnl_free_buf((char **)&s1);
	return (s3);
}
```

