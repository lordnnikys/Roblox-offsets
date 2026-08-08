# Lua_SandBoxThread

Used for activating the sandbox on a new Lua thread, allowing the thread to run scripts with the correct identity and permissions.

Binary search `5F 5F 69 6E 64 65 78 00` (`"__index"` in hex) - go to **second** xref.

```c
.rdata:0000000006B5F3F8 dword_6B5F3F8 dd 6E695F5Fh  ; DATA XREF: sub_5E1560+32↑r
.rdata:0000000006B5F3F8                             ; sub_119E530+3AD↑r ...
```

Second xref is `sub_119E530` - Lua_SandBoxThread.

Offset: **0x119E530**

```c++
lua_State* thread = lua_newthread(mainL);
((void(*)(lua_State*))REBASE(0x119E530))(thread);
```
