A **variadic function** is a function which accepts a **variable number of arguments**. It is characterised by the **"..."** in a function.

```c
int	ft_printf(const char *format, ...);
```

We need to use:
```c
#include <stdarg.h>
```

Give us access to a new type of variable, `**va_list**`_,_ and 3 very useful _macros_: `**va_start**`**,** `**va_arg**` & `**va_end**`

## va_list, va_start, va_end & va_arg
### `va_list` - new object type
`va_list` is an **object type** suitable for holding the information needed by the macros `va_start`, `va_copy,` `va_arg`, and `va_end` (that you will understand in a few minutes). In other words, it is a list that will contain all the dynamic arguments.

To create a variable of this type, you will have to do it the same way as any other variable.

```c
va_list    any_name_you_want;
```

### `**va_start**` **- function macro**

The macro `va_start` function will somehow initialize everything, before we start moving through our variable argument list (va_list). You have to write it like that:

```c
va_start( va_list var, parameterN );

// in our example, it would be:
va_start( args, format);
```

- `var` is a variable of type arg_list (args for us)
- `parameterN` is the named parameter preceding the first dynamic parameter (in our case, with printf, it would be the initial string) - in other words, **it's the mandatory argument**

Its purpose is to set the stage and define which elements will be stable and which will vary. This is when your va_list variable will have all the elements in the table.

`va_start` must be called before any use of `va_arg - otherwise your va_list variable/table will be empty.`

### `**va_arg**` **- function macro**

Now that everything is ready, you can start using and playing with your variable arguments. This can be done with va_arg.

This macro allows access to the arguments of the variadic function. Each time `va_arg` is called, you move to the next argument.

`va_arg` will take as argument first the list of dynamic arguments we had defined at the very beginning (va_list object) and **the type** of the variable of the next argument.

```c
va_arg( va_list var, type_of_the_variable )
```

If we look at an example: 
```c
	va_list args;
	va_start(args, str);
	printf("Hi %s, it's nearly %d o'clock", "Bob", 9);
```
The length of `args` will be 2. There is a string argument in first position and an int argument in second position. 
If you want to access the first argument, you will have to call `va_arg` once and specify the type of the argument. In this case, the first argument is a string, that will be defined by a pointer.

If you want to access the second argument, you do the same thing. But this time the type of the argument is an "int".

```c
// access the first argument (type "string")
va_arg( args,  char * ) // -> "Bob"

// access the second argument (type "int")
va_arg( args, int ) // -> 9
```

### `**va_end**` **- function macro**

Once you have finished your program, don't forget to clean up the object you initialized by calling `va_start`.

`va_end` can modify the object, which was called "args" in our previous example**,** so that it is no longer usable.

```
va_end( va_list var );

// and in our example:
va_end (args);
```

`va_end()` will free the allocated memory.