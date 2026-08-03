# luaC_step
# luaC_barrierback
# luaS_newlstr

luaC_step – runs one step of the garbage collector. Keeps memory usage under control.
luaC_barrierback – GC write barrier (backward direction). Prevents objects that are already scanned from being collected early.
luaS_newlstr – Creates a new interned Lua string. Used every time a string is pushed onto the Lua stack.

From last decompiled code go to 
```c
  {
    sub_4B63510(a1, a2: "not enough memory");
    v11 = 1;
  }
```

Double click sub_4B63510 

```c
    {
      LOBYTE(a2) = 1;
      sub_4B6CD20(a1, a2);
    }
```
sub_4B6CD20 - luaC_step RIGHT under it:

```c
      sub_4B6CAC0(a1, a2: a1, a3: a1 + 8);
    if ( byte_7A36390 == 0
      || (unsigned __int64)(*(_QWORD *)(a1 + 56) + 16LL) <= *(_QWORD *)(*(_QWORD *)(a1 + 72) + 24LL)
      || (unsigned int)sub_4B61A30(a1, a2: 1) != 0 )
    {
```
sub_4B6CAC0- luaC_barrierback and under that you will find:

```c
    {
      v6 = *(_QWORD *)(a1 + 56);
      result = sub_4B9AB60(a1, a2: v2);
      *(_QWORD *)v6 = result;
      *(_DWORD *)(v6 + 12) = 6;
      goto LABEL_16;
    }
```
sub_4B9AB60 - luaS_newlstr
