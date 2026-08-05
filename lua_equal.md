# lua_equal

To find lua_equal search string "_VERSION" go to find xref and decompile:
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
.rdata:0000000006BBE120                 dq offset aRawequal     ; "rawequal"
.rdata:0000000006BBE128                 dq offset sub_4B7DD20
```
Double click sub_4B7DE20, decompile:
```c
__int64 __fastcall sub_4B7DD20(__int64 a1)
{
  int v2; // eax

  sub_4B69480(a1, a2: 1);
  sub_4B69480(a1, a2: 2);
  v2 = sub_4B63970(a1, a2: 1, a3: 2); // <-- lua_equal
  sub_4B62FB0(a1, a2: v2);
  return 1;
}
```

So the offset is 0x4B63970
