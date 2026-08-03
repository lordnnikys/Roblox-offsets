# lua_getmetatable

lua_getmetatable can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 
```c
  if ( a2 >= 0xFFFFD8F1 || a2 == 0 )
    v6 = sub_4B625F0((__int64)a1) + a2 + 1;
  if ( !sub_4B623C0((__int64)a1, a2: v6) ) // <-- lua_getmetatable
    goto LABEL_6;
  sub_4B63510(a1, a2: "__tostring");
```

So the offset is 0x4B623C0
