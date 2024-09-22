```c
/* ************************************************************************** */
/*                                                                            */
/*                                                        :::      ::::::::   */
/*   push_swap.h                                        :+:      :+:    :+:   */
/*                                                    +:+ +:+         +:+     */
/*   By: sfarren <sfarren@student.42malaga.com>     +#+  +:+       +#+        */
/*                                                +#+#+#+#+#+   +#+           */
/*   Created: 2024/09/20 13:41:39 by sfarren           #+#    #+#             */
/*   Updated: 2024/09/21 22:28:55 by sfarren          ###   ########.fr       */
/*                                                                            */
/* ************************************************************************** */

#ifndef PUSH_SWAP_H
# define PUSH_SWAP_H

# include <limits.h>
# include <stdlib.h>
# include <stdbool.h>
# include "./libft/libft.h"

typedef struct s_node
{
	int				value;
	int				count;
	struct s_node	*next;
}				t_node;

typedef struct s_stack
{
	t_node	*top;
}	t_stack;

/**
 * @brief Checks if the given string represents a valid integer.
 *
 * This function verifies if the input string is a valid integer representation.
 *
 * @param str The string to be checked.
 * @return 1 if the string is a valid integer, 0 otherwise.
 */
int		is_valid_integer(const char *str);

/**
 * @brief Converts a string to an integer.
 *
 * This function converts the input string to an integer. It handles optional
 * leading whitespace and an optional plus or minus sign.
 *
 * @param str The string to be converted.
 * @return The integer value of the string.
 */
int		ft_atoi(const char *str);

//  list_utils
/**
 * @brief Creates a new node with the given value.
 *
 * @param value The value to be stored in the new node.
 * @return A pointer to the newly created node.
 */
t_node	*create_node(int value);

/**
 * @brief Inserts a new node with the given value into the linked list.
 *
 * @param head A double pointer to the head of the linked list.
 * @param value The value to be inserted into the new node.
 */
void	insert(t_node **head, int value);

/**
 * @brief Creates a linked list with nodes containing values from 0 to range-1.
 *
 * @param range The number of nodes to be created in the linked list.
 * @return A pointer to the head of the newly created linked list.
 */
t_node	*create_linked_list(int range);
#endif
```