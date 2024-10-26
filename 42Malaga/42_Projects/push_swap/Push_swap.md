*Because Swap_push isn’t as natural*

## Summary:

This project will make you sort data on a stack, with a limited set of instructions, using
the lowest possible number of actions. To succeed you’ll have to manipulate various
types of algorithms and choose the most appropriate solution (out of many) for an
optimised data sorting

Write a program in C called push_swap which calculates and displays
on the standard output the smallest program, made of "Push swap" language instructions,
that sorts the integers received as arguments.

You have at your disposal a set of integer values, 2 stacks, and a set of instructions
to manipulate both stacks.

## The rules
- You have 2 stacks named `a` and `b`.
- At the beginning:
  - The stack `a` contains a random amount of negative and/or positive numbers which cannot be duplicated.
  - The stack `b` is empty.
- The goal is to sort in ascending order numbers into stack `a`. To do so you have the following operations at your disposal:

| Command                   | Description                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------- |
|  `sa` (swap a)            | Swap the first 2 elements at the top of stack `a`. Do nothing if there is only one or no elements. |
|  `sb` (swap b)            | Swap the first 2 elements at the top of stack `b`. Do nothing if there is only one or no elements. |
|  `ss`                     |  `sa` and `sb` at the same time.                                                                   |
|  `pa` (push a)            | Take the first element at the top of `b` and put it at the top of `a`. Do nothing if `b` is empty. |
|  `pb` (push b)            | Take the first element at the top of `a` and put it at the top of `b`. Do nothing if `a` is empty. |
|  `ra` (rotate a)          | Shift up all elements of stack `a` by 1. The first element becomes the last one.                   |
|  `rb` (rotate b)          | Shift up all elements of stack `b` by 1. The first element becomes the last one.                   |
|  `rr`                     |  `ra` and `rb` at the same time.                                                                   |
|  `rra` (reverse rotate a) | Shift down all elements of stack `a` by 1. The last element becomes the first one.                 |
|  `rrb` (reverse rotate b) | Shift down all elements of stack `b` by 1. The last element becomes the first one.                 |
|  `rrr`                    |  `rra` and `rrb` at the same time.                                                                 |


The grade depends on how efficient the program's sorting process is.
- Sorting 3 values: no more than 3 actions.
- Sorting 5 values: no more than 12 actions.
- Sorting 100 values: rating from 1 to 5 points depending on the number of actions:
    - 5 points for less than 700 actions
    - 4 points for less than 900
    - 3 points for less than 1100
    - 2 points for less than 1300
    - 1 point for less than 1500
- Sorting 500 values: rating from 1 to 5 points depending on the number of actions:
    - 5 points for less than 5500 actions
    - 4 points for less than 7000
    - 3 points for less than 8500
    - 2 points for less than 10000
    - 1 point for less than 11500

Validating the project requires at least 80/100.