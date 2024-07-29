- [[get_next_line]]
- [[gnl_strdup]]
- [[gnl_substr]]
- [[gnl_strlen]]
- [[gnl_str_join]]
- [[gnl_free_buf]]
- [[gnl_find_nl]]

```c
/**
 * @brief Reads a line from a file descriptor.
 *
 * @param fd The file descriptor to read from.
 * @return A pointer to the line read from the file descriptor, 
 * or NULL if there are no more lines to read or an error occurs.
 */
char	*get_next_line(int fd);

/**
 * @brief Duplicates a string.
 *
 * @param str The string to duplicate.
 * @return A pointer to the duplicated string.
 */
char	*gnl_strdup(char *str);

/**
 * @brief Extracts a substring from a string.
 *
 * @param s The string to extract the substring from.
 * @param start The starting index of the substring.
 * @param len The length of the substring.
 * @return A pointer to the extracted substring.
 */
char	*gnl_substr(char const *s, unsigned int start, size_t len);

/**
 * @brief Calculates the length of a string.
 *
 * @param str The string to calculate the length of.
 * @return The length of the string.
 */
size_t	gnl_strlen(const char *str);

/**
 * @brief Concatenates two strings.
 *
 * @param s1 The first string.
 * @param s2 The second string.
 * @return A pointer to the concatenated string.
 */
char	*gnl_str_join(char const *s1, char const *s2);

/**
 * @brief Frees the memory allocated for a buffer.
 *
 * @param str The buffer to free.
 * @return A pointer to NULL.
 */
char	*gnl_free_buf(char **str);

/**
 * @brief Finds the index of the first occurrence of a 
 * newline character in a string.
 *
 * @param str The string to search.
 * @return The index of the first occurrence of a 
 * newline character, or -1 if not found.
 */
int		gnl_find_nl(const char *str);

```

additonal functions in `get_next_line.c`
```c
/**
 * Retrieves the next line from a given buffer.
 *
 * @param buf The address of a pointer to the buffer containing the text.
 * @return A pointer to the next line in the buffer, or NULL if there are no more lines.
 */

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
```

```c
/**
 * @brief Creates a new buffer and reads data from a file descriptor into it.
 *
 * This function creates a new buffer and reads data from the 
 * specified file descriptor into it. It continues reading until it 
 * encounters a newline character or reaches the end of the file. 
 * The function dynamically allocates memory for the new buffer and
 * returns it. If an error occurs during the reading process, the 
 * function frees the memory and returns NULL.
 *
 * @param buf The current buffer.
 * @param fd The file descriptor to read from.
 * @return The new buffer containing the read data, or NULL if an error occurred.
 */
char	*gnl_new_buffer(char *buf, int fd)
{
	char	*new_buf;
	int		bytes_read;

	bytes_read = 1;    //init to 1 to begin the loop.
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
```