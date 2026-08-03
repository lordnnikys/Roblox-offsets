# lua_pushnumber

Pushes a double (floating point number) onto the Lua stack.

lua_pushnumber can be found RIGHT above lua_pushstring, so there is already guide on how to find lua_pushstring, you take its offset, in my case its 0x4B63510, press g and go to it. There you will see:

```c
.text:0000000004B634FB sub_4B63490     endp // <-- pushnumber
.text:0000000004B634FB
.text:0000000004B634FB ; ---------------------------------------------------------------------------
.text:0000000004B63500                 db 10h dup(0CCh)
.text:0000000004B63510
.text:0000000004B63510 ; =============== S U B R O U T I N E =======================================
.text:0000000004B63510
.text:0000000004B63510
.text:0000000004B63510 ; __int64 __fastcall sub_4B63510(_QWORD, _QWORD) // <-- pushstring
.text:0000000004B63510 sub_4B63510     proc near               ; CODE XREF: sub_1D22700+16↑p
```
so the offset is sub_4B63490 (0x4B63490)

example of use:
```c++
((void(*)(lua_State*, double))REBASE(0x4B63490))(L, 42.0);
```
