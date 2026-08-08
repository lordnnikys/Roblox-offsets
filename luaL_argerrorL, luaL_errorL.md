# luaL_errorL

Formats an error message and throws it. Full error pipeline: format -> rawcheckstack -> addinfo -> throw.

Search string (shift f12) `"invalid argument #%d (%s expected, got %s)"` go to xref (only 1), decompile (f5):

```c
void __fastcall __noreturn sub_93B8C0(_QWORD *a1, unsigned int a2, const char *a3)
{
  v6 = sub_93B760(a1);
  v7 = sub_937CC0(a1, a2);
  if ( v7 != 0 )
  {
    v8 = (const char *)sub_9556A0(a1, v7);
    if ( v6 != nullptr )
      sub_93C490((__int64)a1, (__int64)"invalid argument #%d to '%s' (%s expected, got %s)", a2, v6, a3, v8);
    sub_93C490((__int64)a1, (__int64)"invalid argument #%d (%s expected, got %s)", a2, a3, v8); // <-- double click sub_93C490
  }
  ...
}
```

Double click `sub_93C490` - luaL_errorL.

Offset: **0x93C490**
