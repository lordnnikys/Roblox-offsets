# lua_replace
# lua_pushcfunction 
# lua_createtable 

This will be dumped with the help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get lua_replace locate:
```c
.rdata:0000000006BBE100                 dq offset aNewproxy     ; "newproxy"
.rdata:0000000006BBE108                 dq offset sub_4B7E0E0
```
Double click the sub_RVA and decompile:
```c
__int64 __fastcall sub_4B7E0E0(_QWORD *a1)
{
  BOOL v2; // ebx

  if ( (unsigned int)sub_4B65630(a1, a2: 1) + 1 > 2 )
    sub_4B6A680(a1, a2: 1, a3: "nil or boolean");
  v2 = sub_4B64E00(a1, a2: 1);
  sub_4B62CA0((__int64)a1, a2: 0, a3: 0x81u); // <-- lua_pushcfunction 
  if ( v2 )
  {
    sub_4B61D80(a1, a2: 0, a3: 0); // <-- lua_createtable 
    sub_4B64920(a1, a2: 4294967294LL); // <-- lua_replace
  }
  return 1;
}
```
