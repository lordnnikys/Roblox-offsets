# lua_error

This will be dumped with hte help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get lua_error locate luaB error:
```c
.rdata:0000000006BBE0B0                 dq offset aError_1      ; "error"
.rdata:0000000006BBE0B8                 dq offset sub_4B7DA50
```
Double click the sub_4B7DA50 and decompile it:
```c
void __fastcall __noreturn sub_4B7DA50(_QWORD *a1)
{
  int v2; // edi

  v2 = sub_4B69AB0(a1, a2: 2, a3: 1);
  sub_4B64BC0(a1, a2: 1);
  if ( sub_4B629A0((__int64)a1, a2: 1) && v2 > 0 )
  {
    sub_4B6A7A0(a1, a2: (unsigned int)v2);
    sub_4B63740(a1, a2: 1);
    sub_4B61C30((__int64)a1, a2: 2);
  }
  sub_4B61F50(a1); // <-- lua_error
} 
```
So the offset is 0x4B61F50. This is luaL_errorL not luaB stuff
