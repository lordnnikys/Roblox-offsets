# lua_topointer

Converts a Lua value at the given index to a pointer (lightuserdata or userdata).

Not a standalone function in this build. Use the formula:

```c
void* lua_topointer(lua_State* L, int idx) {
    TValue* tv = luaA_toobject(L, idx);  // 0x937CC0
    if (tv == NULL) return NULL;
    if (tv->tt == 2)                     // tag 2 = lightuserdata
        return (void*)(*(uint64_t*)tv);
    if (tv->tt == 8 || tv->tt == 9)     // tag 8/9 = userdata
        return ((GCobject*)(*(uint64_t*)tv))->data;
    return NULL;
}
```

Tags: 2 = lightuserdata, 8/9 = userdata.
