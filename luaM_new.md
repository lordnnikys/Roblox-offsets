# luaM_new

To find luaM_new we'll use luaS_newlstr which is sub_4B9AB60 in my case:
```c
  {
LABEL_10:
    if ( a3 <= 0x40000000 )
    {
      v17 = sub_4B8A530(a1, a2: a3 + 25, a3: *(unsigned __int8 *)(a1 + 4)); // <-- luaM_new
      v18 = *(_BYTE *)(*(_QWORD *)(a1 + 40) + 72LL) & 3;
      *(_BYTE *)(v17 + 1) = 6;
      *(_BYTE *)v17 = v18;
      *(_BYTE *)(v17 + 2) = *(_BYTE *)(a1 + 4);
```

So the offset is 0x4B8A530
