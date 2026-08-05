# lua_getfenv

To find lua_getfenv search string "_VERSION" go to find xref and decompile:
```c
{
  sub_4B63740(a1, a2: -10002);
  sub_4B64870(a1, a2: 4294957294LL, a3: &off_603A3C8);
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);
  sub_4B63370((__int64)a1, a2: (__int64)"Luau");
  sub_4B64870(a1, a2: 4294957294LL, a3: "_VERSION");
```
Find 3rd sub in the table and double click off_6BBE0A0, find:
```c
.rdata:0000000006BBE0D0                 dq offset aGetfenv      ; "getfenv"
.rdata:0000000006BBE0D8                 dq offset sub_4B7DBE0
```
Double click sub_4B7DBE0, decompile:
```c
__int64 __fastcall sub_4B7DBE0(_QWORD *a1)
{
  sub_4B7E170(a1, a2: 1);
  if ( sub_4B628C0((__int64)a1, a2: 0xFFFFFFFFLL) )
    sub_4B63740(a1, a2: -10002);
  else
    sub_4B621A0(a1, a2: -1); // <-- lua_getfenv
  sub_4B64AC0((__int64)a1, a2: 0xFFFFFFFFLL, a3: 0);
  return 1;
}
```

So the offset is sub_4B621A0
