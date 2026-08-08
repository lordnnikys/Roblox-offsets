# luaL_checklstring

Checks that the argument at a given index is a string and returns it.

Not a standalone function in this build. Reconstruct from two pieces:

```c
const char* luaL_checklstring(lua_State* L, int arg, size_t* len) {
    TString* ts = luaA_toobject(L, arg);     // 0x937CC0
    if (ts == NULL || ts->tt != 6)
        luaL_typerrorL(L, arg, "string");    // 0x93B8C0
    if (len) *len = ts->len;
    return ts->data;
}
```

Both functions are in your dump:  
- `luaA_toobject`  = 0x937CC0 (guide: "invalid argument" string -> sub_93B8C0 -> find call)
- `luaL_typerrorL` = 0x93B8C0 (guide: "invalid argument #%d" string -> first xref)
