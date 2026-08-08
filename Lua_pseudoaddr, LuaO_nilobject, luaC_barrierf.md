# Lua_pseudoaddr / LuaO_nilobject / luaC_barrierf

Lua_pseudoaddr - used for converting a Lua stack index (like -1 or -10002) into a real memory address.
LuaO_nilobject  - A global "nil" placeholder that is returned when a stack slot is empty.
luaC_barrierf   - GC write barrier for functions.

To dump all three you do same as Lua_SandBoxThread (`"__newindex"` string -> second xref -> sub_119E530) but decompile (f5) and find `sub_958BE0` which sets the metatable. Double click it and decompile:

At the top of sub_958BE0 you'll see:
```c
    v4 = (int *)&unk_610B898;  // LuaO_nilobject
```

And nearby:
```c
    unk_610B760               // LuaH_dummynode
```

So **LuaO_nilobject** = offset `0x610B898`  
So **LuaH_dummynode** = offset `0x610B760`

---

For Lua_pseudoaddr, stay in sub_958BE0 and look for the function that handles index -10002 / -10001. Ctrl+F for `-10002`:

```c
    case -10002:
      v8 = a1[14];
      *(QWORD*)(v8 + 1200) = a1[1];
      *(DWORD*)(v8 + 1212) = 7;
    case -10001: ...
    case -10000: ...
```

Double click the containing function which is `sub_937C00` — that is **Lua_pseudoaddr**.

Offset: **0x937C00**

---

For luaC_barrierf, in sub_958BE0 or sub_94C250 (luaV_settable, called from same chain) decompilation, find the readonly check:
```c
    if ( (*(_BYTE *)(*(_QWORD *)v4 + 4LL) != 0 )
      sub_977130(a1);       // luaG_readonlyerror
```
After the value is written, the GC barrier is called to mark the object gray.
Double click it — that's luaC_barrierf.
