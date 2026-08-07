# luau_load

Search for "bytecode corrupted", go to its xref and just copy sub_97C200 well in my case it is:
```c
.rdata:0000000006B60030 aSBytecodeCorru db '%s: bytecode corrupted',0
.rdata:0000000006B60030                                         ; DATA XREF: sub_97C200+233↑o
```

Jump to sub_97C200 and press ctrl x, second, 3rd, 4th 5th xrefs are the luau_load, which in my case is:
```c
Down    o    sub_227CC60+19E    lea     rdx, sub_97C200
```

So the offset is 0x227CC60
