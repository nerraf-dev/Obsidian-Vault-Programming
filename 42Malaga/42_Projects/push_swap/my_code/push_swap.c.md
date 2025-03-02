```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   push_swap.c                                        :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/09/19 21:00:45 by sfarren           #+#    #+#             */
/*   Updated: 2024/10/28 11:10:27 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#include "../includes/push_swap.h"

/*
The `is_sorted` function checks if an array of integers is sorted in ascending order. It iterates through the array and compares each element with the next one. If it finds any element that is greater than the next one, it returns `false`, indicating that the array is not sorted. If the loop completes without finding any such elements, it returns `true`.
*/
bool	is_sorted(int *int_array, int arr_size)
{
	int	i;

	i = 0;
	while (i < arr_size - 1)
	{
		if (int_array[i] > int_array[i + 1])
			return (false);
		i++;
	}
	return (true);
}

/*
The `handle_error` function is used to handle errors by printing an error message, freeing allocated memory, and exiting the program. It takes a message string, a split array, and an integer array as parameters. If the split array is not null, it frees it using the `free_split` function. Similarly, if the integer array is not null, it frees it. Finally, it exits the program with a status of 1.
*/

void	handle_error(const char *message, char **split, int *int_array)
{
	ft_printf("Error: %s\n", message);
	if (split)
	{
		free_split(split);
	}
	if (int_array)
	{
		free(int_array);
	}
	exit(1);
}

/*
The `main` function is the entry point of the program. It starts by declaring variables for an integer array, its size, and two stack nodes (`stack_a` and `stack_b`). It then parses the command-line arguments using the `argument_parser` function to populate the integer array and its size. If the array is already sorted, the program returns 0 and exits. Otherwise, it initializes `stack_a` with the integer array and `stack_b` as an empty stack. If the initialization of `stack_a` fails, it calls `handle_error` to handle the memory allocation failure. Depending on the size of the array, it either calls `sort_small` or `sort_big` to sort the stacks. Finally, it frees the allocated memory for the integer array and the stacks before returning 0 to indicate successful execution
*/

int	main(int argc, char **argv)
{
	int				*int_array;
	int				arr_size;
	t_stack_node	*stack_a;
	t_stack_node	*stack_b;

	arr_size = 0;
	int_array = argument_parser(argc, argv, &arr_size);
	if (is_sorted(int_array, arr_size))
		return (0);
	stack_a = initialise_stack(int_array, arr_size);
	stack_b = initialise_stack(NULL, 0);
	if (!stack_a)
		handle_error("Memory allocation failed", NULL, int_array);
	if (arr_size <= 5)
		sort_small(&stack_a, &stack_b);
	else
		sort_big(&stack_a, &stack_b);
	free(int_array);
	free_stack(&stack_a);
	free_stack(&stack_b);
	return (0);
}

```

