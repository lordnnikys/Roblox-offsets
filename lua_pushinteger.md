# lua_pushinteger

Pushes an integer onto the Lua stack. Tag 4 (LUA_TINTEGER in Roblox).

Find lua_pushnumber first (`"__index"` bytes -> SandBoxThread -> sub_119DE10 -> sub_938E80). lua_pushinteger is the next function right below it at `0x938EF0`:

```c
__int64 __fastcall sub_938EF0(__int64 a1, __int64 a2)
{
  if (stack_full) { GC_step(); stack_overflow_error(); }
  *(QWORD*)L->top = a2;              // store integer
  *(DWORD*)(L->top + 12) = 4;        // tag = LUA_TINTEGER
  L->top += 16;
}
```

Copy sub_938EF0 and jump to it, and scroll bit up (well actually down, binary goes bottom to up so scrolling down in binary means looking up, KEEP IN MIND!!!)
```asm
.text:0000000000938E80 arg_0           = qword ptr  8
.text:0000000000938E80
.text:0000000000938E80                 mov     [rsp+arg_0], rbx // <-- you're somewhere here
```

Scroll down until you see big SUBROUTINE text with ==:
```asm
.text:0000000000938EF0 ; =============== S U B R O U T I N E =======================================
.text:0000000000938EF0
.text:0000000000938EF0
.text:0000000000938EF0 ; __int64 __fastcall sub_938EF0(__int64, __int64)
.text:0000000000938EF0 sub_938EF0      proc near               ; CODE XREF: sub_223CA40+378↓p
.text:0000000000938EF0                                         ; sub_223CA40+3A7↓p ...
.text:0000000000938EF0
.text:0000000000938EF0 arg_0           = qword ptr  8
.text:0000000000938EF0
.text:0000000000938EF0                 mov     [rsp+arg_0], rbx
```

Offset: **0x938EF0**

```c++
((void(*)(lua_State*, long long))REBASE(0x938EF0))(L, 42);
```
