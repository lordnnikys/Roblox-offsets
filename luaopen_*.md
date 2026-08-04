# luaopen_*

To find luaopen_* search for string "_VERSION", first xref will be it:
```c
.rdata:0000000006BBE318 aVersion_3      db '_VERSION',0         ; DATA XREF: sub_4B7E520+56↑o // <-- luaopen_*
```

Or decompile:
```c
__int64 __fastcall sub_4B7E520(_QWORD *a1)
```

So the offset is 0x4B7E520
