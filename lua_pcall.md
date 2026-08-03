# lua_pcall

lua_pcall can be found by searching string `"cannot resume non-suspended"`, there is only 1 xref, go to it and decompile: 
```c
__int64 __fastcall sub_4B68410(__int64 a1, __int64 a2, unsigned int a3)
```

So the offset is 0x4B68410
