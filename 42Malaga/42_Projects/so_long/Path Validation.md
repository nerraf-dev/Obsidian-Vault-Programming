
|        | **0** | 1   | 2   | **3** | **4** | **5** | **6** | **7** | **8** | **9** | **10** | **11** |
| ------ | ----- | --- | --- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ | ------ |
| **0**  | 1     | 1   | 1   | 1     | 1     | 1     | 1     | 1     | 1     | 1     | 1      | 1      |
| **1**  | 1     | E   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **2**  | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **3**  | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **4**  | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **5**  | 1     | 0   | 0   | C     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **6**  | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **7**  | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | C     | 0      | 1      |
| **8**  | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **9**  | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0      | 1      |
| **10** | 1     | 0   | 0   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | P      | 1      |
| **11** | 1     | 1   | 1   | 1     | 1     | 1     | 1     | 1     | 1     | 1     | 1      | 1      |

Get the starting position, P. 
`[10,10]`
 
```c
// Node structure for the queue
// The x and y coordinates represent the position in the map
// The next pointer points to the next node in the queue
// The queue is used to implement the flood-fill algorithm
typedef struct s_queue_node
{
	int					x;
	int					y;
	// char				type;	// P, C, E, 1, 0
	struct s_queue_node	*next;
}	t_queue_node;

// Queue structure
// The front pointer points to the first node in the queue
// The rear pointer points to the last node in the queue
typedef struct s_queue
{
	t_queue_node	*front;
	t_queue_node	*rear;
}	t_queue;
```

```c
int	flood_fill(t_game *game_data, int **visited)
{
	// Implement the flood-fill algorithm here
	// Check if the current position is valid and not visited
	// Mark the current position as visited
	// Check if the current position is the exit or a collectible
	// Recursively call flood_fill for adjacent cells (up, down, left, right)
	// If the exit is reached, return success
	// If all collectibles are collected, return success
	// If the queue is empty and the exit is not reached, return failure
}
```



- Initialise the queue
	- allocate memory for the queue, `malloc(sizeof(t_queue));`
	- initialise `front` and `rear` as `NULL`
- Create and initialise the first node
	- allocate memory for the node
	- set x and y to start position
	- set next to `NULL`
- Set queue `front` and `rear` to the new `node`
- Mark the position as `1` in `visited`
- While the queue is not empty:
	- dequeue the current node


dequeue:
- go to `node` position, e.g. `[2,1]`
- get all valid positions around the node pos.
	- Up:`[x-1,y]`
	- Down:`[x+1,y]`
	- Left:`[x,y-1]`
	- Right:`[x,y+1]`
- 
