

```c

#include <stdio.h>

int	main(int argc, char **argv)
{
	int	i;

	if (argc == 1)
	{
		printf("No arguments provided.\n");
	}
	else
	{
		printf("Arguments provided:\n");
		i = 1;
		while (i < argc)
			printf("%s\n", argv[i++]);
	}
	return (0);
}
```

