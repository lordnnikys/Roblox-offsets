# luaG_runerror

luaG_runerror - formats and throws ALL luau errors, every error you've ever seen is from this function.

To get luaG_runerror search string "cannot resume non-suspended coroutine":
```asm
.rdata:0000000006B5F140 aCannotResumeNo db 'cannot resume non-suspended coroutine',0
.rdata:0000000006B5F140                                         ; DATA XREF: sub_948D40:loc_948D5D↑o
.rdata:0000000006B5F140                                         ; sub_22FC0F0:loc_22FC393↑o ...
```
First xref is it, well you can decompile:
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
