# luau_load

luau_load - loads Lua bytecode into a Lua state. Also called LuaVM_Load by Roblox.

Search string (shift f12) `"bytecode type version mismatch"` go to xref, that is `sub_97C200` (bytecode reader):

```c
.rdata:0000000006B60088 aSBytecodeTypeV db '%s: bytecode type version mismatch (expected [%d..%d], got %d)',0
.rdata:0000000006B60088                                         ; DATA XREF: sub_97C200+1B0↑o
```

Press X on `sub_97C200`, second xref is luau_load:

```c
Down    o    sub_227CC60+19E    lea     rdx, sub_97C200
```

Double click `sub_227CC60` - luau_load.

Offset: **0x227CC60**
