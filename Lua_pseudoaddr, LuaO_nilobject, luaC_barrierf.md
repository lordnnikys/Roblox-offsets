# Lua_pseudoaddr / LuaO_nilobject / luaC_barrierf

Lua_pseudoaddr - converts a Lua stack index (like -1 or -10002) into a real memory address.
LuaO_nilobject  - global "nil" placeholder returned when a stack slot is empty.
luaC_barrierf   - GC write barrier for functions.

All three from one starting point.

Binary search `5F 5F 69 6E 64 65 78 00` (`"__index"` in hex) - go to **second** xref (SandBoxThread). Decompile (f5).

In the decompilation you'll see `"__index"` loaded as a string:

```c
    v52 = 7;
    strcpy((char *)v51, "__index");
    sub_119DE10(a1, a3, v51, v48);      // <-- double click sub_119DE10
```

Decompile sub_119DE10. Inside, near the end, find the call that writes the metatable entry:

```c
  v69 = v35;
  v70 = 6;
  result = sub_958BE0(a1, v68, &v69, v65);  // <-- double click sub_958BE0
  *(_QWORD *)(a1 + 72) -= 16LL;
  return result;
```

Decompile sub_958BE0. Scroll to the top:

```c
__int64 __fastcall sub_958BE0(__int64 a1, ...)
{
  v4 = (int *)&unk_610B898;            // <-- LuaO_nilobject
  v5 = *(_QWORD *)(a1 + 112);
  ...
```

And near the end of the function, after the table value is written:

```c
    if ( *(_BYTE *)(*(_QWORD *)v54 + 4LL) != 0 )
      sub_977130(a1);                  // luaG_readonlyerror
    *(_QWORD *)(*(_QWORD *)v54 + 16LL) = a2;
  }
  sub_94C420(a1, a2);                  // <-- double click = luaC_barrierf
```

**LuaO_nilobject** - the `unk_` at the top of sub_958BE0.  
**luaC_barrierf** - the function called after the value is written. Inside it checks `G->gcstate` then marks the object.

## Lua_pseudoaddr

In sub_958BE0, Ctrl+F for `-10002`:

```c
    case -10002:                       // LUA_REGISTRYINDEX
    case -10001:                       // LUA_GLOBALSINDEX
    case -10000:                       // LUA_ENVIRONINDEX
    default:
      // negative -> top-relative
      // positive -> base-relative
```

Double click the function containing this switch - **Lua_pseudoaddr**.

This build:
- Lua_pseudoaddr  = `0x937C00`
- LuaO_nilobject  = `0x610B898`
- luaC_barrierf   = `0x94C420`
