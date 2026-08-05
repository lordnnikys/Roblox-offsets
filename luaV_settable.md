# luaV_settable

Search string `"__index"` second xref, decompile:
```c
__int64 __fastcall sub_1DA9D90(__int64 a1)
{
  sub_4B61D80(a1, a2: 0, a3: 0);
  sub_4B61D80(a1, a2: 0, a3: 0);
  sub_1D22700(a1, a2: 0xFFFFFFFFLL);
  sub_4B63370(a1, a2: "__index", a3: 7);
  sub_4B63740(a1, a2: 4294957294LL);
  sub_4B64B40(a1, a2: 4294967293LL);
  return sub_4B64920(a1, a2: 4294967294LL);
}
```
Double click sub_4B64B40 and search for:
```c
  }
  result = sub_4B96010(a1, a2: v4, a3: v3 - 32, a4: v3 - 16); // <-- luaV_settable
  *(_QWORD *)(a1 + 56) -= 32LL;
  return result;
```

So the offset is 0x4B96010
