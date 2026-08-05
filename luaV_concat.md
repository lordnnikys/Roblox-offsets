# luaV_concat 

Use already known lua_concat, in my case 0x4B61C30, jump to it and decompile:
```c
  {
    if ( *(_QWORD *)(*(_QWORD *)(a1 + 40) + 8LL) >= **(_QWORD **)(a1 + 40) )
      sub_4B6CD20(a1, a2: 1);
    if ( (*(_BYTE *)a1 & 4) != 0 )
      sub_4B6CAC0(a1, a2: a1, a3: a1 + 8);
    sub_4B95390( // <-- luaV_concat 
      a1,
      a2: (unsigned int)v2,
      a3: (unsigned int)((__int64)(*(_QWORD *)(a1 + 56) - *(_QWORD *)(a1 + 64)) >> 4) - 1);
    *(_QWORD *)(a1 + 56) += 16 - 16 * v2;
  }
```

So the offset is 0x4B95390
