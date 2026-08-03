# coroutineL

To dump coroutineL search string for "coroutine" go to the first (the only code xref, not rdata) and decompile it:
```c
__int64 __fastcall sub_4B7EEA0(_QWORD *a1)
{
  sub_4B69E30(a1, a2: "coroutine", a3: &off_6BBE370);
  sub_4B63030(
    (_DWORD)a1,
    a2: (unsigned int)qword_4B7EDF0,
    a3: (unsigned int)"resume",
    a4: 0,
    a5: (__int64)qword_4B7ED00);
  sub_4B64870(a1, a2: 4294967294LL, a3: "resume");
  return 1;
}
```
double click off_6BBE370

There you will see tables similarly to luaB:
```c
.rdata:0000000006BBE370                                         ; "create"
.rdata:0000000006BBE378                 dq offset sub_4B7E710
.rdata:0000000006BBE380                 dq offset aRunning_1    ; "running"
.rdata:0000000006BBE388                 dq offset sub_4B7E7D0
.rdata:0000000006BBE390                 dq offset aStatus       ; "status"
.rdata:0000000006BBE398                 dq offset sub_4B7E6A0
.rdata:0000000006BBE3A0                 dq offset aWrap_0       ; "wrap"
.rdata:0000000006BBE3A8                 dq offset sub_4B7E750
.rdata:0000000006BBE3B0                 dq offset aYield        ; "yield"
.rdata:0000000006BBE3B8                 dq offset sub_4B7E7B0
.rdata:0000000006BBE3C0                 dq offset aIsyieldable  ; "isyieldable"
.rdata:0000000006BBE3C8                 dq offset sub_4B7E800
.rdata:0000000006BBE3D0                 dq offset aClose_0      ; "close"
.rdata:0000000006BBE3D8                 dq offset sub_4B7E830
```

sub_4B7E710 - coroutine create, etc...
