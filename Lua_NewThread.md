# Lua_NewThread

Used for creating new coroutine (thread) from existing state. Required for sandboxed execution for user scripts.

To dump lua_newthread you find string "script start" (shift f12) go to **second** xref and call under it will be lua_newthread: 
```c
.text:0000000001DB7E6E                 lea     r8, aScriptStart ; "Script Start"
.text:0000000001DB7E75                 mov     rdx, r15
.text:0000000001DB7E78                 lea     rcx, [rbp+340h+var_270]
.text:0000000001DB7E7F                 call    sub_1D528B0 <-- ignore this
.text:0000000001DB7E84                 nop
.text:0000000001DB7E85                 mov     rcx, r15
.text:0000000001DB7E88                 call    sub_4B62BD0 <-- lua_newthread
```
.text:0000000001DB7E88                 call    sub_4B62BD0 -> lua_newthread. You can ignore that it takes 3 args, thats lua_newthread.

So the offset is 0x4B62BD0
