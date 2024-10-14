
On macOS:
use `leaks` to help check for memory leaks 
```bash
leaks -atExit -- ./push_swap 8 9 7   
```

Hopefully see something like:
```bash
----

leaks Report Version: 4.0, multi-line stacks
Process 8293: 184 nodes malloced for 11 KB
Process 8293: 0 leaks for 0 total leaked bytes.

```

## lldb
`lldb` helpful for debugging.

Run `llbd ./push_swap` 
```bash
lldb ./push_swap                  
(lldb) target create "./push_swap"
Current executable set to '/.../push_swap' (x86_64).
(lldb) 
```

then 
```bash
(lldb) run 9 7 8
```

 or pass the args in initially `lldb ./push_swap 9 8 7` the `run`


