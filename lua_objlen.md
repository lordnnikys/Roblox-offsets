# lua_objlen

To find lua_objlen search string "_VERSION" go to find xref and decompile:
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
.rdata:0000000006BBE150                 dq offset aRawlen       ; "rawlen"
.rdata:0000000006BBE158                 dq offset sub_4B7DE20
```
Double click sub_4B7DE20, decompile:
```c
__int64 __fastcall sub_4B7DE20(_QWORD *a1)
{
  int v2; // eax

  if ( (unsigned int)sub_4B65630(a1, a2: 1) - 6 > 1 )
    sub_4B69390(a1, a2: 1, a3: "table or string expected");
  v2 = sub_4B62F20(a1, a2: 1); // <-- lua_objlen
  sub_4B63270((__int64)a1, a2: v2);
  return 1;
}
```

So the offset is 0x4B62F20
