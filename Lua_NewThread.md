# Lua_NewThread

ROBLOX INLINED THIS FUNCTION. STILL CAN BE REPLICATED
```c
  ; thread = luaM_new(L, 128, 0) via G->frealloc
   mov r8d, 0x80
   mov rcx, rsi           ; L
   call [G->frealloc]     ; rax = new lua_State*
   mov rbx, rax

   ; GC header
   mov cl, [G + 0x10]     ; G->currentwhite
   and cl, 3
   mov [rbx+1], cl         ; marked
   mov byte [rbx], 0x0A   ; tt = LUA_TTHREAD (at offset 0 now!)
   mov al, [rsi+6]         ; L->memcat
   mov [rbx+2], al         ; memcat

   ; State setup
   mov rax, [rsi+0x70]     ; G
   mov [rbx+0x70], rax     ; thread->global = G
   mov [rbx+0x50], r14     ; base_ci = NULL
   lea r12, [rbx+0x40]
   mov [r12], r12d         ; base_ci = thread+0x40
   mov [rbx+8], r14        ; stack = NULL
   mov [rbx+0x28], r14     ; openupval = NULL
   mov [rbx+0x44], r14d    ; nCcalls = 0
   mov [rbx+0x30], r14     ; top = NULL
   mov [rbx+3], 0          ; status = 0
   mov [rbx+0x58], r14     ; errorJmp = NULL
   mov [rbx+0x18], r14     ; gt = NULL
   mov [rbx+0x78], r14     ; cb = NULL
   mov [rbx+0x20], r14     ; registry = NULL
   mov [rbx+6], al         ; memcat again
   ; ...then allocates stack (0x180 bytes) and callinfo (0x2D0 bytes)
```
