# lua_gcinfo

This will be dumped with hte help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get luaL_gcinfo locate luaB gcinfo:
```c
.rdata:0000000006BBE0C0                 dq offset aGcinfo       ; "gcinfo"
.rdata:0000000006BBE0C8                 dq offset sub_4B7DE80
```
Double click the sub_4B7DA50 and decompile it:
```c
__int64 __fastcall sub_4B7DE80(__int64 a1)
{
  int v2; // eax

  v2 = sub_4B61F60(a1, a2: 3, a3: 0); // <-- lua_gc
  sub_4B63270(a1, a2: v2);
  return 1;
}
```
So the offset is 0x4B61F60 . This is not luaB stuff
