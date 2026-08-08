# lua_pushstring

Pushes a C string onto the Lua stack as an interned TString.

Not a standalone function in this build - the TString creation logic is inlined into lua_getfield (0x93E0C0). Use the formula:

```c
void lua_pushstring(lua_State* L, const char* s) {
    size_t len = strlen(s);
    TString* ts = luaS_newlstr(L, s, len);
    *(QWORD*)L->top = ts;
    *(DWORD*)(L->top + 12) = 6;    // tag = LUA_TSTRING
    L->top += 16;
}
```

TString is created by computing a 32-bit hash of the string, looking it up in G->stringtable, and allocating a new GC object (tag at offset 0 is 6) if not found.

Alternatively, find it through the `"__index"` chain to lua_getfield (0x93E0C0) and extract the inline TString creation block.
