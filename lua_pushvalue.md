# lua_pushvalue

This will be dumped with the help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get lua_pushvalue locate:
```c
.rdata:0000000006BBE0D0                 dq offset aGetfenv      ; "getfenv"
.rdata:0000000006BBE0D8                 dq offset sub_4B7DBE0
```
Double click the sub_RVA and decompile:
```c
__int64 __fastcall sub_4B7DBE0(_QWORD *a1)
{
  sub_4B7E170(a1, a2: 1);
  if ( sub_4B628C0((__int64)a1, a2: 0xFFFFFFFFLL) )
    sub_4B63740(a1, a2: -10002); // <-- lua_pushvalue
  else
    sub_4B621A0(a1, a2: -1);
  sub_4B64AC0((__int64)a1, a2: 0xFFFFFFFFLL, a3: 0);
  return 1;
}
```
