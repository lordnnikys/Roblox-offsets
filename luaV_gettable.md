# luaV_gettable

Use already known lua_gettable offset, jump to it in my case its sub_4B62550 and decompile:
```c

    if ( (unsigned __int64)v5 >= v4 )
      v5 = &unk_6BC0438;
  }
  sub_4B959E0(a1, a2: v5, a3: v4 - 16, a4: v4 - 16); // <-- luaV_gettable
  return *(unsigned int *)(a1[7] - 4LL);
}
```

So the offset is 0x4B959E0
