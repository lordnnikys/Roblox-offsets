# lua_bit32

To find lua_bit32 search for string "bit32", first xref will be it:
```c
.rdata:0000000006BBF084 aBit32          db 'bit32',0            ; DATA XREF: sub_4B84E20+B↑o // <-- lua_bit32
```
Or decompile:
```c
__int64 __fastcall sub_4B84E20(_QWORD *a1)
{
  sub_4B69E30(a1, a2: "bit32", a3: &off_6BBEEB0);
  return 1;
}
```

So the offset is 0x4B84E20
