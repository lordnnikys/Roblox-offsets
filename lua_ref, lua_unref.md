# lua_ref
# lua_unref

To find these search string `"__mode"` go to second xref and decompile:
```c
    sub_4B625F0(a1: (__int64)v2);
    sub_4B61D80(a1: v2, a2: 0, a3: 0);
    sub_4B63740(a1: v2, a2: -1);
    sub_4B64920(a1: v2, a2: 4294967294LL);
    sub_4B63510(a1: v2, a2: &unk_6040018);
    sub_4B64870(a1: v2, a2: 4294967294LL, a3: "__mode");
    sub_4B63BF0(a1: v2, a2: -10000, a3: *(_DWORD *)(a1 + 24));
    if ( (unsigned int)sub_4B65630(a1: v2, a2: -1) != 0 )
    {
      sub_4B64870(a1: v2, a2: 4294967294LL, a3: "result");
      sub_4B64A40(a1: v2, a2: 0xFFFFFFFFLL, a3: 1);
      *(_DWORD *)(a1 + 28) = sub_4B642F0(a1: v2, a2: 0xFFFFFFFFLL); // <-- lua_ref
      sub_4B64BC0(a1: v2, a2: -2);
      v3 = *(unsigned int *)(a1 + 24);
      if ( byte_7F2DF28 != 0 )
      {
        *(_DWORD *)(a1 + 24) = sub_4B656B0(a1: (__int64)v2, a2: v3); // <-- lua_unref
      }
      else
      {
        sub_4B656B0(a1: (__int64)v2, a2: v3); // <-- lua_unref
        *(_DWORD *)(a1 + 24) = -1;
      }
```

So the offsets are:
lua_ref - 0x4B642F0
lua_unref - 0x4B656B0
