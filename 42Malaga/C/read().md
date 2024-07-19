SYNOPSIS 

```c
#include <unistd.h>
ssize_t read(int** _fd_**, void** _buf_**[.**_count_**], size_t** _count_**);
```

_fs_ is the file descriptor, 

from [Wikipedia](https://en.wikipedia.org/wiki/File_descriptor)

**File descriptors** are a part of the [POSIX](https://en.wikipedia.org/wiki/POSIX "POSIX") [API](https://en.wikipedia.org/wiki/Application_programming_interface "Application programming interface"). Each Unix [process](https://en.wikipedia.org/wiki/Process_(computing) "Process (computing)") (except perhaps [daemons](https://en.wikipedia.org/wiki/Daemon_(computer_software) "Daemon (computer software)")) should have three standard POSIX file descriptors, corresponding to the three [standard streams](https://en.wikipedia.org/wiki/Standard_streams "Standard streams"):

|Integer value|Name|<[unistd.h](https://en.wikipedia.org/wiki/Unistd.h "Unistd.h")> symbolic constant|<[stdio.h](https://en.wikipedia.org/wiki/Stdio.h "Stdio.h")> file stream|
|---|---|---|---|
|0|[Standard input](https://en.wikipedia.org/wiki/Stdin "Stdin")|STDIN_FILENO|stdin|
|1|[Standard output](https://en.wikipedia.org/wiki/Stdout "Stdout")|STDOUT_FILENO|stdout|
|2|[Standard error](https://en.wikipedia.org/wiki/Stderr "Stderr")|STDERR_FILENO|stderr|