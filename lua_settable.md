# lua_settable

To find lua_settable we'll use Lua_SandBoxThread offset which is in my case 0x1DA9D90, decompile it and find:
```c
__int64 __fastcall sub_1DA9D90(__int64 a1)
{
  sub_4B61D80(a1, a2: 0, a3: 0);
  sub_4B61D80(a1, a2: 0, a3: 0);
  sub_1D22700(a1, a2: 0xFFFFFFFFLL);
  sub_4B63370(a1, a2: "__index", a3: 7);
  sub_4B63740(a1, a2: 4294957294LL);
  sub_4B64B40(a1, a2: 4294967293LL); // <-- lua_settable
  return sub_4B64920(a1, a2: 4294967294LL);
}
```

So the offset is 0x4B64B40
