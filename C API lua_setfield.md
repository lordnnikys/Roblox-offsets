# lua_setfield

That isnt normal lua_setfield, that is C API setfield which prefereably you should use in your executors, anyways to get it we already know luaG_readonlyerror from previous guides and it is sub_4B6B440, to get lua_setfield we jump to sub_4B6B440 (g in ida and ghidra) second CODE xref, not loc but sub. Go to second xref and decompile it:
```c
__int64 __fastcall sub_4B64050(_QWORD *a1, int a2, __int64 a3)
```

sub_4B64050 = 0x4B64050 is lua_setfield but c API
