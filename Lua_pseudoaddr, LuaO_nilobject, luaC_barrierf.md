# Lua_pseudoaddr / LuaO_nilobject / luaC_barrierf

Lua_pseudoaddr - converts a Lua stack index (like -1 or -10002) into a real memory address.
LuaO_nilobject  - global "nil" placeholder returned when a stack slot is empty.
luaC_barrierf   - GC write barrier for functions. Marks objects so they don't get collected early.

All three from one starting point.

Binary search `5F 5F 69 6E 64 65 78 00` (`"__index"` in hex) - go to **second** xref (SandBoxThread). Decompile (f5).

Find the call that sets `__index` / `__newindex`:

```c
  sub_XXXXXX(a1, a3, "__index", 8);    // <-- double click
```

Decompile. Find the next function called near the end:

```c
  sub_XXXXXX(a1, slot, &tvalue, top);  // <-- double click
```

Decompile this final function. All three offsets are inside:

```c
__int64 __fastcall sub_XXXXXX(__int64 a1, ...)
{
  null_ptr = (type *)&unk_XXXXXXXX;    // <-- LuaO_nilobject

  // ... table ops ...

  if ( *(BYTE *)(*(QWORD *)table + 4) != 0 )
    sub_XXXXXX(L);                      // luaG_readonlyerror

  sub_XXXXXX(L, value);                // <-- double click = luaC_barrierf
}
```

**LuaO_nilobject** - the `unk_` at top of function.  
**luaC_barrierf** - the function called after readonly check, right after value write.  
Double click it - inside it checks `G->gcstate` then marks the object.

## Lua_pseudoaddr

In the same decompilation, Ctrl+F for `-10002`:

```c
    case -10002:                       // LUA_REGISTRYINDEX
    case -10001:                       // LUA_GLOBALSINDEX
    case -10000:                       // LUA_ENVIRONINDEX
    default:
      // negative -> top-relative
      // positive -> base-relative
```

Double click the function - **Lua_pseudoaddr**.

This build:
- Lua_pseudoaddr  = `0x937C00`
- LuaO_nilobject  = `0x610B898`
- luaC_barrierf   = `0x94C420`
