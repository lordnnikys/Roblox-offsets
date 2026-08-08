# lua_rawcheckstack / luaD_throw / luaG_addinfo

lua_rawcheckstack - makes sure the Lua stack has space for new values before pushing.
luaD_throw - performs the actual stack unwinding when a Lua error is thrown.
luaG_addinfo - adds source file name and line number to error messages.

All three found from luaG_runerror.

Search string `"attempt to modify a readonly table"` (1 match) - go to xref. Decompile (f5):

```c
void __fastcall __noreturn sub_977130(__int64 a1)
{
  sub_977900(a1, a2: "attempt to modify a readonly table");  // <-- double click
}
```

Double click `sub_977900`, then double click `sub_978940`:

```c
void __noreturn sub_978940(__int64 a1, char *a2, ...)
{
  char Buffer[520];
  va_list va;

  va_start(va, a2);
  sub_976F20(Buffer, 0x200u, a2, va);   // vsnprintf - formats the error
  sub_938180(a1, 1);                    // <-- lua_rawcheckstack
  sub_978320(a1, Buffer);               // <-- luaG_addinfo
  sub_945D80(a1, 2);                    // <-- luaD_throw
}
```

- `sub_976F20` - Microsoft CRT vsnprintf, not a Lua function
- `sub_938180` - **lua_rawcheckstack**  (0x938180)
- `sub_978320` - **luaG_addinfo**       (0x978320)
- `sub_945D80` - **luaD_throw**         (0x945D80)
