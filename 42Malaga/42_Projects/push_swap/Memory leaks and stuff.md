
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


If you see something like:
```bash
Process 8727 launched: '/.../push_swap' (x86_64)
arr: 9 - rank[0] = 2
arr: 7 - rank[1] = 0
arr: 8 - rank[2] = 1
Value: 9, Rank: 2
Value: 7, Rank: 0
Value: 8, Rank: 1
Process 8727 exited with status = 0 (0x00000000) 
```

nothing major happened.