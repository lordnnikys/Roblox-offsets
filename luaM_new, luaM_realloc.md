# luaM_new
# luaM_realloc

To find luaM_new decompile luaG_runerror (we already know its 0x9485A0) find, lines ~120 to ~160 :
```c
LABEL_12:
    if ( v7 > 0x40000000 )
      goto LABEL_95;
    v18 = *(_BYTE *)(a1 + 6);
    v19 = v7 + 25;
    v20 = *(_QWORD *)(a1 + 112);
    v74 = v18;
    if ( v7 + 24 >= 0x400 || ((v21 = *((char *)&unk_7A2DCF0 + v19 + 160)) & 0x80u) != 0LL )
    {
      v27 = (_DWORD *)sub_954490(a1, a2: (int)v20 + 800, a3: (int)v7 + 89, a4: v19, a5: 1); // <-- luaM_realloc
      v17 = v27 + 16;
      v27[12] -= v27[9];
      ++v27[13];
    }
    else
    {
      v22 = 8 * v21;
      v23 = *(_QWORD *)(8 * v21 + v20 + 424);
      if ( v23 == 0 )
        v23 = sub_954540(a1, a2: (int)v20 + 424, a3: (int)v20 + 800, a4: v21, a5: 0); // <-- luaM_new 
      v24 = *(int *)(v23 + 48);
      if ( (int)v24 < 0 )
      {
        v17 = *(_DWORD **)(v23 + 40);
        *(_QWORD *)(v23 + 40) = *((_QWORD *)v17 + 1);
      }
      else
      {
        v17 = (_DWORD *)(v24 + v23 + 64);
        LODWORD(v24) = v24 - *(_DWORD *)(v23 + 36);
        *(_DWORD *)(v23 + 48) = v24;
```

So the offset is 0x954540
And luaM_realloc is 0x954490
