# lua_next

This will be dumped with the help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get lua_next locate luaB next:
```c
.rdata:0000000006BBE0F0                 dq offset aNext_4       ; "next"
.rdata:0000000006BBE0F8                 dq offset sub_4B7DF30
```

Double click sub_4B7DF30 and decompile it:
```c
__int64 __fastcall sub_4B7DF30(_QWORD *a1)
{
  sub_4B696A0(a1, a2: 1, a3: 7);
  sub_4B64BC0(a1, a2: 2);
  if ( (unsigned int)sub_4B62E30((__int64)a1, a2: 1) != 0 ) // <-- lua_next
    return 2;
  sub_4B63430(a1);
  return 1;
}
```

So the offset is 0x4B63A40. This is **LUA**_next, not luaB_next
