# lua_encodepointer

lua_pushstring can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 
```c
        v13 = sub_4B65290(a1, a2);
        v14 = sub_4B61E40((__int64)a1, a2: v13); // <-- lua_encodepointer
        v15 = (int *)sub_4B618C0(a1, a2);
        if ( v15 != nullptr )
```

So the offset is 0x4B61E40
