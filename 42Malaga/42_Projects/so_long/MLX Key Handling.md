
The key handler can work with `keycode` or `keysym`. 

```c
// Hook key press events to the handle_keypress function
	mlx_hook(mlx_win, 2, 1L << 0, (int (*)(int, void *))handle_keypress, params);
```

```c
// Function to handle key presses
int	handle_keypress(int keysym, void *params[2])
{
	if (keysym == XK_Escape)  // Alternative :(keycode == 65307)
		close_window(params);
	return (0);
}
```

