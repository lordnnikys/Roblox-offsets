# lua_settop

Sets the Lua stack top to a specific index. Grows or shrinks the stack as needed.

Not a standalone function in this build - inlined into callers. Use the formula:

```c
void lua_settop(lua_State* L, int idx) {
    L->top = L->base + 16 * idx;
    // if idx > current top, fill gaps with nils (tag 0)
    // if idx < current top, just move top pointer
}
```

L->top  at offset 0x48
L->base at offset 0x60

Index -1 = top-relative pop, index -10002 = registry, etc.
