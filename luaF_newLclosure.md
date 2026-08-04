# luaF_newLclosure

To dump luaF_newLclosure search string "%s: bytecode corrupted" go to its xref decompile and find (near end):
```c
  while ( v228 < 0 );
  if ( (*(_BYTE *)v3 & 4) != 0 )
    sub_4B6CAC0(a1: v3, a2: v3, a3: v3 + 8); 
  v229 = sub_4B93D70(a1: v3, a2: 0, a3: v249); // <-- luaF_newLclosure
  v230 = *(_QWORD *)(v3 + 56);
  *(_QWORD *)v230 = v229;
  *(_DWORD *)(v230 + 12) = 8;
  v231 = *(_QWORD *)(v3 + 56);
``` 

So the offset is 04B93D70
