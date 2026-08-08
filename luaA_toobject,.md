# luaA_toobject

Converts a Lua stack index to a TValue pointer. Returns nullptr if the slot is nil.

Search string (shift f12) `"invalid argument #%d (%s expected, got %s)"` go to xref, decompile (f5):

```c
void __fastcall __noreturn sub_93B8C0(_QWORD *a1, unsigned int a2, const char *a3)
{
  v6 = sub_93B760(a1);
  v7 = sub_937CC0(a1, a2);            // <-- luaA_toobject
  if ( v7 != 0 )
  {
    v8 = (const char *)sub_9556A0(a1, v7);
    ...
  }
}
```

Double click `sub_937CC0`:

```c
void *__fastcall sub_937CC0(__int64 a1, __int64 idx)
{
  if ( idx <= 0 ) {
    if ( idx <= -10000 ) result = sub_937C00(a1, idx);  // pseudoaddr
    else result = *(a1 + 72) + 16 * idx;                 // top-relative
  } else {
    result = *(a1 + 96) + 16 * idx - 16;                 // base-relative
  }
  if ( result == &unk_610B898 ) return nullptr;          // nil -> null
  return result;
}
```

Offset: **0x937CC0**
