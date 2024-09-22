

```c
#include <stdio.h>

int	main(int argc, char **argv)
{
	if (argc == 1)
	{
		printf("No arguments provided.\n");
	}
	else
	{
		printf("Arguments provided:\n");
		for (int i = 1; i < argc; i++)
		{
			printf("%d\n", (int)argv[i]);
		}
	}
	return (0);
}
```

