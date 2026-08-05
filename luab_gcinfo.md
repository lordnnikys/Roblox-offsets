# luab_gcinfo

This will be dumped with hte help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get luaL_gcinfo locate luaB gcinfo:
```
c.rdata:0000000006BBE0C0                 dq offset aGcinfo       ; "gcinfo"
.rdata:0000000006BBE0C8                 dq offset sub_4B7DE80
```

So the offset is 0x4B7DE80.
