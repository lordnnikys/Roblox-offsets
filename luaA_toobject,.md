# luaA_toobject

lua_pushstring can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 
```c
        v14 = sub_4B61E40((__int64)a1, a2: v13);
        v15 = (int *)sub_4B618C0(a1, a2); // <-- luaA_toobject
        if ( v15 != nullptr )
          v16 = (const char *)sub_4B8AD70((__int64)a1, a2: v15);
```

So the offset is 0x4B618C0
