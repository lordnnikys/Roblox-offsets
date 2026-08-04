# lua_rawget

This will be dumped with hte help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get lua_rawget locate luaB rawget:
```c
.rdata:0000000006BBE130                 dq offset aRawget       ; "rawget"
.rdata:0000000006BBE138                 dq offset sub_4B7DD70
```
Double click the sub_4B7DD70 and decompile it:
```c
__int64 __fastcall sub_4B7DD70(_QWORD *a1)
{
  sub_4B696A0(a1, a2: 1, a3: 7);
  sub_4B69480(a1, a2: 2);
  sub_4B64BC0(a1, a2: 2);
  sub_4B63A40(a1, a2: 1); // <-- lua_rawget
  return 1;
}
```
So the offset is 0x4B63A40. This is **LUA**_rawget, not luaB_rawget
