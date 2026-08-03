# luaC_step

lua_gc can be found by going to RVA we found in lua_gc, which in my case is: 4B61F60, go here and decompile:
```c
          v15 = sub_4B6CD20(a1, a2: 0); // <-- luaC_step
          v7 = *(_BYTE *)(v3 + 73);
          v11 += v15;
```
Well... It's the only offset in this code.

So the offset is 0x4B6CD20
