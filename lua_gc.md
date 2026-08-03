# lua_gc
lua_gc can be found by searching string "collectgarbage must be called with 'count'" there is only 1 xref, go to it and decompile: 
```c
  v9 = sub_4B61F60(a1, a2: 3, a3: 0); // <-- lua_gc
  sub_4B63490(a1, a2: (double)v9);
  return 1;
```

So the offset is 0x4B61F60
