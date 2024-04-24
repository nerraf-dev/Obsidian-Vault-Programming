The function `ft_atoi` stops processing the string at the first non-digit character after the optional sign due to the structure of the while loop on line 27.

Here's how it works:

1. After processing any leading whitespace and an optional sign character, the function enters a while loop that continues as long as the current character (`str[i]`) is a digit (i.e., between '0' and '9' inclusive).
    
2. Inside the loop, the function multiplies the current result by 10 and adds the numeric value of the current character. This effectively appends the digit to the end of the number being built. The index `i` is then incremented to move to the next character.
    
3. If the next character is not a digit, the condition of the while loop (`str[i] >= '0' && str[i] <= '9'`) will be false, so the loop will terminate.
    
4. The function then returns the result, multiplied by the sign. This is the final step of the function, so it does not process any more characters after the first non-digit character.

```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   ft_atoi.c                                          :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/04/11 19:53:26 by sfarren           #+#    #+#             */
/*   Updated: 2024/04/13 19:53:19 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

/* Converts a string to an integer.
 * takes a string `str` as input and converts it to an integer.
 * Skips any leading whitespace chars & checks for an optional sign (+/-).
 * The resulting integer is multiplied by the sign and returned.
 *
 * @param str The string to be converted to an integer.
 * @return The converted integer value.
*/
int	ft_atoi(char *str)
{
	int	i;
	int	sign;
	int	result;

	i = 0;
	sign = 1;
	result = 0;
	//loop over sting whilst there is a whitespace char (as per isspace())
	while (str[i] == ' ' || (str[i] >= 9 && str[i] <= 13))
		i++;
	
	if (str[i] == '-' || str[i] == '+')
	{
		if (str[i] == '-')
			sign = -1;
		i++;
	}

	while (str[i] >= '0' && str[i] <= '9')
	{
		result = result * 10 + (str[i] - '0');
		i++;
	}

	return (result * sign);
}
```