# luaG_runerror

luaG_runerror - formats and throws ALL luau errors, every error you've ever seen is from this function.

In previous guide i said that `luaG_readonlyerror` is useless. But from it we can dump luaG_runerror!

To dump it go to Lus_SandBoxThread which you already know how to dump from my guides:


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

 double click **sub_4B64920** 

And find this block: 
```c
    if ( *(_BYTE *)(*(_QWORD *)v4 + 4LL) != 0 )
      sub_4B6B440(a1);
    *(_QWORD *)(*(_QWORD *)v4 + 16LL) = v5;
  }
```
  
  that is **luaG_readonlyerror**, then, double click **sub_4B6B440**: 

```c
void __fastcall __noreturn sub_4B6B440(__int64 a1)
{
  sub_4B6B470(a1, a2: "attempt to modify a readonly table");
}
```

sub_4B6B470 - luaG_runerror so the offset is 0x4B6B470
