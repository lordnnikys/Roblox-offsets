# luaL_tolstring

Converts any Lua value at a given index to its string representation. Used by print() internally.

Search string (shift f12) `"print"` go to xref. In the data table, the **next qword** after the "print" string pointer is luaB_print:

```c
.rdata:0x61F5AC0  dq 0x6B72534    ; "print" string pointer
.rdata:0x61F5AC8  dq 0x4151D20    ; luaB_print
```

Decompile luaB_print (0x4151D20):

```c
  v4 = (const void *)sub_943ED0(a1, v1, &ElementCount);  // <-- luaL_tolstring
```

Double click `sub_943ED0` - luaL_tolstring.

Offset: **0x943ED0**
