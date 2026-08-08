# luaG_runerrorL

luaG_runerrorL - formats error message, adds source info, then throws the error. Full error pipeline.

Search string (shift f12) `"%s:%d: %s"` go to **first** xref - that is `sub_978320` (luaG_addinfo). Decompile it to confirm:

```c
__int64 __fastcall sub_978320(__int64 a1, const char *a2)
{
  ...
  sub_977900(a1, (__int64)"%s:%d: %s", v6, v8, v3);
  ...
}
```

While you're at decompiled code, scroll all the way up and click once on sub_978320, press x and first xref is our target:
```c
void __noreturn sub_978940(__int64 a1, char *a2, ...)
{
  char Buffer[520];
  va_list va;

  va_start(va, a2);
  sub_976F20(Buffer, 0x200u, a2, va);
  sub_938180(a1, 1);
  sub_978320(a1, Buffer);
  sub_945D80(a1, 2);
}
```

sub_978940 - luaG_runerrorL

Offset: **0x978940**
