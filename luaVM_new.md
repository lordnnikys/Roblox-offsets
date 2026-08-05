# luaVM_new 

To find luaVM_new decompile lua_newthread (we already know its 0x4B62BD0):
```c
  {
    sub_4B99F50(a1, a2: "stack overflow");
    sub_4B61F50(a1);
  }
  v2 = sub_4B66090(a1); // <-- luaVM_new
  v3 = *(_QWORD *)(a1 + 56);
  v4 = v2;
  *(_QWORD *)v3 = v2;
```

So the offset is 0x4B66090
