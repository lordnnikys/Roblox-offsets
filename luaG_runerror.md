# luaG_runerror

luaG_runerror - formats and throws ALL luau errors, every error you've ever seen is from this function.

To get luaG_runerror we will use lua_resume which is at 0x948D40 in my case, decompile it and find:

```c
    return sub_9485A0(a1, a2: "cannot resume non-suspended coroutine"); // <-- luaG_runerror
  if ( a2 != 0 )
  {
    v5 = *(_WORD *)(a2 + 48);
    *(_WORD *)(a1 + 48) = v5;
    if ( v5 >= 0xC8u )
      return sub_9485A0(a1, a2: "C stack overflow"); // <-- luaG_runerror
``` 

So the offset is 0x9485A0
