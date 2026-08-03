# lua_getfield

lua_getfield can be found by searching string "_VERSION", there is only 1 xref, go to it and decompile: 
find this string:
```c
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0); // <-- luaL_register
```
Double click sub_4B69E30:
```c
    sub_4B622B0((__int64)a1, a2: -1, a3: (__int64)a2);
    if ( (unsigned int)sub_4B65630(a1, a2: -1) != 7 )
    {
```

So the offset is 0x4B622B0
