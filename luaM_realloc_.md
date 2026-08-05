# `luaM_realloc_`

To find luaM_new we'll use luaS_newlstr which is sub_4B9AB60 in my case:
```c
      v21 = *(_DWORD *)(v19 + 56);
      if ( *(_DWORD *)(v19 + 60) <= (unsigned int)v21 || v21 > 0x3FFFFFFF )
        return v17;
      v22 = 2 * v21;
      if ( (unsigned __int64)v22 <= 0x1FFFFFFFFFFFFFFFLL )
      {
        v23 = (_QWORD *)sub_4B8A470(a1, a2: 8LL * v22, a3: 0); // <-- 
        v24 = *(_QWORD *)(a1 + 40);
        v25 = v23;
        if ( v22 > 0 )
          memset(Dst: v23, Val: 0, Size: 8LL * v22);
        v26 = *(_DWORD *)(v24 + 56);
```

So the offset is 0x4B8A470
