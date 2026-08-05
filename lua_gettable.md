# lua_gettable

search for string "invalid use of '%c' in replacement string" go to its xref decompile, and find near start:
```c
        sub_4B69760(a1: *(_QWORD *)(a1 + 32), a2: "unfinished capture");
      }
      if ( v19 == -2 )
      {
        sub_4B63270(a1: (__int64)v5, a2: *(_DWORD *)(a1 + 48) - *(_DWORD *)(a1 + 8) + 1);
LABEL_23:
        sub_4B62550(a1: v5, a2: 3); // <-- lua_gettable
        goto LABEL_24;
      }
      v18 = *(_QWORD *)(a1 + 48);
    }
    else
    {
```

So the offset is 0x4B62550
