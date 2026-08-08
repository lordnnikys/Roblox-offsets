# lua_gc

Controls the garbage collector. Takes (L, int what, int data).

Not a single standalone function in this build. The GC is split across:

- `luaC_step`   = 0x94BEC0 — runs one GC step (what=LUA_GCSTEP)
- `sub_94C250`  = 0x94C250 — runs full GC cycle (what=LUA_GCCOLLECT)
- `sub_94C4A0`  = 0x94C4A0 — GC throughput calculation (what=LUA_GCCOUNT)

Use the formula:
```c
int lua_gc(lua_State* L, int what, int data) {
    switch (what) {
        case LUA_GCSTOP:     G->gcstate = 0; return 0;
        case LUA_GCRESTART:  G->gcstate = 1; return 0;
        case LUA_GCCOLLECT:  sub_94C250(L, data, 0); return 0;
        case LUA_GCCOUNT:    return G->totalbytes >> 10;
        case LUA_GCSTEP:     sub_94BEC0(L, data); return 0;
        default: return 0;
    }
}
```
