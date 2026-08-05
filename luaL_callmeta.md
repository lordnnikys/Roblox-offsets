# luaL_getmetafield

This will be dumped with the help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get luaL_callmeta locate:
```c
.rdata:0000000006BBE0E0                 dq offset aGetmetatable ; "getmetatable"
.rdata:0000000006BBE0E8                 dq offset sub_4B7DAC0
```
Double click the sub_RVA and decompile:
```c
__int64 __fastcall sub_4B7DAC0(__int64 a1)
{
  sub_4B69480(a1, a2: 1);
  if ( sub_4B623C0(a1, a2: 1) )
    sub_4B698E0(a1, a2: 1, a3: "__metatable"); // <-- luaL_getmetafield 
  else
    sub_4B63430(a1);
  return 1;
} 
```
So the offset is 0x4B698E0
