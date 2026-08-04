# luaL_checkinteger

To find luaL_checkinteger we'll use already known offset luaopen_bit32 which in my case is at 0x4B84E20, jump to it and look down, you'll see:
```c
.text:0000000004B84E50
.text:0000000004B84E50 ; =============== S U B R O U T I N E =======================================
.text:0000000004B84E50
.text:0000000004B84E50
.text:0000000004B84E50 ; __int64 __fastcall sub_4B84E50(__int64)
.text:0000000004B84E50 sub_4B84E50     proc near               ; DATA XREF: .rdata:0000000006BBF098↓o
.text:0000000004B84E50                                         ; .rdata:0000000006BBF268↓o
.text:0000000004B84E50
.text:0000000004B84E50 arg_8           = qword ptr  10h
.text:0000000004B84E50
```

Decompile it:
```c
__int64 __fastcall sub_4B84E50(__int64 a1)
{
  int v2; // eax

  v2 = sub_4B69590(a1, a2: 1); // <-- luaL_checkinteger
  if ( v2 < 0 )
    sub_4B69390(a1, a2: 1, a3: "size");
  sub_4B62B20(a1, a2: v2);
  return 1;
}
```
So the offset is 0x4B69590
