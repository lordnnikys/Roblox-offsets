# lua_topointer

lua_topointer can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 
```c
        sub_4B65200(a1, a2, a3: 0);
        sub_4B9B0D0(a1: v17);
        sub_4B63370((__int64)a1, a2: (__int64)v17);
        break;
      case 4u:
        v12 = sub_4B64EE0(a1, a2, a3: 0); // <-- lua_lua_topointer
        sub_4B9B000(a1: v17, a2: v12);
        sub_4B63370((__int64)a1, a2: (__int64)v17);
        break;
```

So the offset is 0x4B64EE0
