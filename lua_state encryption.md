# lua_state encryption

To find lua_state encryption we'll use offset we already know, luaS_newlstr which is sub_4B63510 decompile it and find this:
```c
      v14 = *(_QWORD *)v8;
      v8 += 3;
      v9 = (v13 ^ (v14 + v9)) - __ROR4__(v13, 14);
      v10 = (v9 ^ (HIDWORD(v14) + v10)) - __ROR4__(v9, 11);
      v11 = (v10 ^ v13) - __ROL4__(v10, 7);
      --v12;
    }
    while ( v12 != 0 );
  }
  for ( ; v4 != 0; --v4 )
    v11 ^= ((unsigned int)v11 >> 2) + 32 * v11 + *((unsigned __int8 *)v8 + v4 - 1);
  v15 = *(_QWORD *)(a1 + 40); // <-- lua_state encryption
  v16 = *(_QWORD *)(*(_QWORD *)(v15 + 64) + 8 * (v11 & (unsigned __int64)(*(int *)(v15 + 56) - 1LL)));
  if ( v16 == 0 )
  {
LABEL_10:
    if ( a3 <= 0x40000000 )
    {
```

To get an actual offset click on 40 once and press h, ida will change it to 0x28, that is your offset
