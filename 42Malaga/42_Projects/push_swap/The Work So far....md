```c
void	sort_big(t_stack_node **stack_a, t_stack_node **stack_b)
{
	int		len;

	ft_printf("---STACK A START---\n");
	print_stack(*stack_a, "A");
	len = stack_size(*stack_a);
	// First 2 elements are pushed to stack B no matter what!
	if (len-- > 3)
		pb(stack_a, stack_b);
	if (len-- > 3)
		pb(stack_a, stack_b);
	sort_two(stack_b);
	while (len-- > 3 && !stack_sorted(*stack_a))
	{
		initialise_nodes_a(*stack_a, *stack_b);
		push_a_to_b(stack_a, stack_b);
	}
	sort_small(stack_a, stack_b);
	while (stack_b)
	{
		initialise_b_nodes(*stack_a, *stack_b);
		push_b_to_a(stack_a, stack_b);
	}
	current_index(*stack_a);
	min_to_top(stack_a);
}
```

Array:

| **A** | 5   | 3   | 7   | 1   | -9  | 42  |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** |     |     |     |     |     |     |

sort_big:
Push first 2 nodes to b, and sort in descending order:

```
pb
pb
sb
```

| **A** | 7   | 1   | -9  | 42  |     |     |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** | 5   | 3   |     |     |     |     |

`while (len-- > 3 && !stack_sorted(*stack_a))`

set_target_a

iteration 1:

| **A** | 7   | 1   | -9  | 42  |     |     |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** | 5   | 3   |     |     |     |     |


---STACK A - AFTER INITIALISE NODES---
Stack A:
Value: 7
Index: 0
Next Node: 0x55555555b420
Next Node Value: 1
Prev Node: 0x55555555b480
Target Node Value: 5

Value: 1
Index: 1
Next Node: 0x55555555b3f0
Next Node Value: -9
Prev Node: 0x55555555b450
Target Node Value: 5

Value: -9
Index: 2
Next Node: 0x55555555b3c0
Next Node Value: 42
Prev Node: 0x55555555b420
Target Node Value: 5

Value: 42
Index: 3
Next Node: (nil)
Next Node Value: -99999
Prev Node: 0x55555555b3f0
Target Node Value: 5

---STACK B - AFTER INITIALISE NODES---
Stack B:
Value: 5
Index: 0
Next Node: 0x55555555b480
Next Node Value: 3
Prev Node: 0x55555555b4b0
Target Node Value: -99999

Value: 3
Index: 1
Next Node: (nil)
Next Node Value: -99999
Prev Node: 0x55555555b4b0
Target Node Value: -99999

Cost Calculation:

| **A** | 7   | 1   | -9  | 42  |     |     |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** | 5   | 3   |     |     |     |     |
```c
while (stack_a)
	{
		stack_a->cost = stack_a->index;
		if (!(stack_a->above_median))
			stack_a->cost = len_a - (stack_a->index);
		if (stack_a->target->above_median)
			stack_a->cost += stack_a->target->index;
		else
			stack_a->cost += len_b - (stack_a->target->index);
		stack_a = stack_a->next;
	}
```

The first iteration begins with the cost for `stack_a[0]`.

```
Value: 7
Index: 0
Next Node Value: 1
Target Node Value: 5
```

cost = index = 0
the node is above the median.
cost = cost + target index = 0 + 0

```
Value: 1
Index: 1
Next Node Value: -9
Target Node Value: 5
```
For 1:
cost = 1
Above Median: True
Cost = index (1) + target index (0) = 1

```
Value: -9
Index: 2
Next Node Value: 42
Target Node Value: 5
```
For 9:
cost = 2
Above Median: True
Cost = index (2) + target index (0) = 2
```
Value: 42
Index: 3
Next Node: (nil)
Next Node Value: -99999
Target Node Value: 5
```
For 42:
cost = 3
Above Median: False
Cost = index (3) + target index (0) = 3

| **A** | 7   | 1   | -9  | 42  |     |     |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** | 5   | 3   |     |     |     |     |
PB as 7 is the lowest cost node

| **A** | 1   | -9  | 42  |     |     |     |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** | 7   | 5   | 3   |     |     |     |

sort three on stack a

| **A** | -9  | 1   | 42  |     |     |     |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** | 7   | 5   | 3   |     |     |     |

Push_prep 
```c

void	push_prep(t_stack_node **stack,	t_stack_node *top_node,
						char stack_name)
{
	while (*stack != top_node) //Check if the required node is not already the first node
	{
		if (stack_name == 'a') //If not, and it is stack `a`, execute the following
		{
			if (top_node->above_median)
				ra(stack);
			else
				rra(stack);
		}
		else if (stack_name == 'b') //If not, and it is stack `b`, execute the following
		{
			if (top_node->above_median)
				rb(stack);
			else
				rrb(stack);
		}
	}
}
```
pushing from b to a, using `push_prep(stack_a, (*stack_b)->target, 'a');`

`while (*stack != top_node)` `*stack_a` value would be -9 node, `*top_node` would be `*stack_b->target` which is th e`42` node.
`42` top_node is the largest value in `stack_a` and so is as the bottom of the stack, below the median. `rra` command is issued, bringing 42 to the top to allow the 7 to be pushed on top.

| **A** | 7   | -9  | 1   | 42  |     |     |
| ----- | --- | --- | --- | --- | --- | --- |
| **B** | 5   | 3   |     |     |     |     |
