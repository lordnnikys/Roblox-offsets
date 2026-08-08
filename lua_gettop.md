# lua_gettop

Returns the number of elements on the Lua stack.

Inlined in this build - no standalone function. Use the formula directly:

```c
int lua_gettop(lua_State* L) {
    return (*(QWORD*)(L + 0x48) - *(QWORD*)(L + 0x60)) >> 4;
}
```

L + 0x48 = L->top  
L + 0x60 = L->base

You can verify the offsets via `lua_absindex` (0x938660) which uses the same computation:

```c
if (a2 >= 0xFFFFD8F1 || a2 == 0)
    return a2 + (*(QWORD*)(L + 0x48) - *(QWORD*)(L + 0x60)) >> 4 + 1;
```

Search string `"'__tostring' must return a string"` go to xref - the function using `lua_absindex` confirms the offset values.
