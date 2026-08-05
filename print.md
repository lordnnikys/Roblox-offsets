# print

To dump print search for string "invalid password from %s", xref and decompile it:
```c
    v14 = sub_A2D800(Dst: v62);
    if ( *(_QWORD *)(v14 + 24) >= 0x10u )
      v14 = *(_QWORD *)v14;
    sub_4C27BF0(a1: 4, a2: (__int64)"Invalid password from %s", (const char *)v14); // <-- print
    if ( v63 >= 0x10 )
    {
      if ( v63 + 1 >= 0x1000 && (unsigned __int64)(v62[0] - *(_QWORD *)(v62[0] - 8LL) - 8LL) > 0x1F )
        invalid_parameter_noinfo_noreturn();
```

So the offset is 0x4C27BF0
(credits 1360939069663875132, not bitdancer)
