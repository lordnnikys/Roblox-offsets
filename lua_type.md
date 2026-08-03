# lua_type

lua_type can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 
```c
  if ( (unsigned int)sub_4B65630(a1, a2: 0xFFFFFFFFLL) == 0 ) // <-- lua_type
  {
    sub_4B64BC0(a1, a2: -3);
LABEL_6:
```

So the offset is 0x4B65630
