# luaL_errorL

lua_pushstring can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 
```c
  result = sub_4B64FF0((__int64)a1, a2: -1, a3);
  if ( result == 0 )
    sub_4B69760((__int64)a1, a2: "'__tostring' must return a string"); // <-- luaL_errorL
  return result;
```

so the offset is 0x4B69760
