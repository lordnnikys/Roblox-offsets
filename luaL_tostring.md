# luaL_tostring

luaL_tostring can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 
```c
__int64 __fastcall sub_4B69F70(_QWORD *a1, unsigned int a2, _QWORD *a3)
```
Well... It's literally first line.

So the offset is 0x4B69F70
