# Lua_NewThread

Used for creating new coroutine (thread) from existing state. Required for sandboxed execution for user scripts.

**In this build lua_newthread has been inlined into ScriptContext. There is no standalone function.**

To find it you find string (shift f12) "Script Start" go to first xref, that is sub_2345A40 (ScriptContext). Decompile it (f5), then scroll to the thread creation or Ctrl+F in disassembly for "80h" and find:

```asm
.text:0000000002345F99                 mov     r8d, 80h
.text:0000000002345F9F                 mov     rcx, rsi
.text:0000000002345FA2                 call    cs:__guard_dispatch_icall_fptr
.text:0000000002345FA8                 mov     rax, [rsi+70h]
.text:0000000002345FAC                 movzx   ecx, byte ptr [rax+10h]
.text:0000000002345FB0                 and     cl, 3
.text:0000000002345FB3                 mov     [rbx+1], cl
.text:0000000002345FB6                 mov     byte ptr [rbx], 0Ah
```

At 0x2345F99 it allocates 128 bytes for the lua_State through robux's allocator.
At 0x2345FB6 it sets the thread tag (0xA) at **offset 0** — this was at offset +1 in the old build.

This code allocates a new lua_State and initializes all its fields inline:

```c
// allocation: 128 bytes via G->frealloc
// GC header:    tag 0xA at offset 0, marked bits at offset +1
// State:        global_State copied from parent, base_ci set
// All fields:   stack=NULL, top=NULL, status=0, nCcalls=0, etc
// Stack:        0x180 bytes allocated
// CallInfo:     0x2D0 bytes allocated
```

Since there's no standalone function you can call, you need to either:
1. Replicate the 20-line block from ScriptContext as shellcode
2. Or manually call luaM_new(128), set tag to 0xA, copy G pointer, and push onto the parent stack

Offset: **NOT A SINGLE FUNCTION** — inlined at `0x2345F99` inside `sub_2345A40`

Key change from old build: GC tag at offset **0**, not +1.
