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

Copy

```
va_list    any_name_you_want;

// we will call it args for the next example:
va_list    args;
```