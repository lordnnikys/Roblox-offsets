# luaC_step / luaC_barrierback

luaC_step        - runs one step of the garbage collector.
luaC_barrierback - GC write barrier (backward). Prevents scanned objects from being collected early.

Both found together. Search string (shift f12) `"stack overflow"` go to any xref, decompile (f5), find:

```c
    LOBYTE(a2) = 1;
    sub_94BEC0(a1, a2);                // <-- luaC_step
```

Double click `sub_94BEC0` - luaC_step. Offset: **0x94BEC0**

luaC_barrierback is right next to it. Jump to `0x94C480` and decompile:

```c
__int64 __fastcall sub_94C480(__int64 a1, __int64 a2, _QWORD *a3)
{
  v3 = G;
  *(a2 + 1) &= ~4u;                    // clear black bit on object
  *a3 = *(v3 + 64);                    // save old gray root
  *(v3 + 64) = a2;                     // wire object into gray list
  return *a3;
}
```

Offset: **0x94C480**
