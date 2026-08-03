# lua_xmove

To dump lua_xmove you need coroutine.create (sub_4B7E710 in my case), jump to sub_4B7E710 (g and paste sub_4B7E710), decompile it:
```c
__int64 __fastcall sub_4B7E710(__int64 a1)
{
  __int64 v2; // rax

  sub_4B696A0(a1, a2: 1, a3: 8); // check arg1 is thread/function
  v2 = sub_4B62BD0(a1); // lua_newthread we got this already
  sub_4B65980(a1, a2: v2, a3: 1); // <-- lua_xmove(L_main, L_new, index)
  return 1;
}
```

so the offset is 0x4B65980
