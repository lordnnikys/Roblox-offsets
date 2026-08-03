# luaL_checklstring

luaL_checklstring can be found by searching string "collectgarbage must be called with 'count'" there is only 1 xref, go to it and decompile: 
```c
  {
    v3 = sub_4B69B10(a1, a2: 1, a3: (__int64)"collect", a4: nullptr); // <-- luaL_checklstring
    v4 = 0;
    while ( 1 )
    {
```

So the offset is 0x4B69B10
