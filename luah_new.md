# luah_new

To find luah_new we'll use already known offset lua_createtable which is in my case sub_4B61D80, jump to it, decompile and find:
```c
    sub_4B61F50(a1);
  }
  v6 = *(_QWORD *)(a1 + 56);
  result = sub_4B8C810(a1, a2: v4, a3); // <-- luah_new
  *(_QWORD *)v6 = result;
  *(_DWORD *)(v6 + 12) = 7;
  *(_QWORD *)(a1 + 56) += 16LL;
  return result;
```

So the offset is 0x4B8C810
