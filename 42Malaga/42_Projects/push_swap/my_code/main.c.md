The check_duplicates function takes an array of integers and its size as arguments. It iterates through the array using two nested loops to compare each element with every other element. If a duplicate is found, it returns true; otherwise, it returns false.

The print_error_and_exit function is used to print an error message and terminate the program. It takes a message and an optional array pointer. If the array pointer is not NULL, it frees the allocated memory before exiting the program with a status code of 1.

The parse_arguments function converts command-line arguments into an array of integers. It allocates memory for the array based on the number of arguments. If memory allocation fails, it calls print_error_and_exit. It then iterates through the arguments, checks if each one is a valid integer using is_valid_integer, and converts them to integers using ft_atoi. If any argument is invalid, it prints an error message and exits.

The main function is the entry point of the program. It first checks if there are any command-line arguments provided. If not, it prints an error message and exits. It then calls parse_arguments to convert the arguments into an array of integers. It stores the starting address of the array in arr_start for later use. It checks for duplicates in the array using check_duplicates. If duplicates are found, it prints an error message and exits. Finally, it prints each integer in the array and frees the allocated memory before exiting the program.

```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   main.c                                             :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/09/20 13:39:44 by sfarren           #+#    #+#             */
/*   Updated: 2024/09/22 12:41:12 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#include "push_swap.h"

bool	check_duplicates(int *arr, int size)
{
	int	i;
	int	j;

	i = 0;
	while (i < size - 1)
	{
		j = i + 1;
		while (j < size)
		{
			if (arr[i] == arr[j])
				return (true);
			j++;
		}
		i++;
	}
	return (false);
}

void	print_error_and_exit(const char *message, int *arr)
{
	ft_printf("%s\n", message);
	if (arr)
		free(arr);
	exit(1);
}

int	*parse_arguments(int argc, char **argv)
{
	int	*arr;
	int	i;

	arr = (int *)malloc((argc - 1) * sizeof(int));
	if (!arr)
		print_error_and_exit("Memory allocation failed", NULL);
	i = 0;
	while (i < argc - 1)
	{
		if (!is_valid_integer(argv[i + 1]))
			print_error_and_exit("Invalid integer", arr);
		arr[i] = ft_atoi(argv[i + 1]);
		i++;
	}
	return (arr);
}

int	main(int argc, char **argv)
{
	int	*arr;
	int	*arr_start;

	if (argc <= 1)
		print_error_and_exit("No arguments provided", NULL);
	arr = parse_arguments(argc, argv);
	arr_start = arr;
	if (check_duplicates(arr, argc - 1))
		print_error_and_exit("Error: Duplicate number", arr);
	while (*arr)
	{
		ft_printf("%d\n", *arr);
		arr++;
	}
	free(arr_start);
	return (0);
}

```