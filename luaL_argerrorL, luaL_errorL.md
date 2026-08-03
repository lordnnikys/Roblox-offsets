# luaL_argerrorL
# luaL_errorL

To find these offsets search for string (f12) search for "level must be non-negative" go to first xref and decompile:

```c
    sub_4B69390(a1, a2: 1, a3: "level must be non-negative");
  if ( (unsigned int)sub_4B6B860(a1, a2: (unsigned int)v5, a3: "f", a4: v7) == 0 )
    sub_4B69390(a1, a2: 1, a3: "invalid level");
  result = (_OWORD *)sub_4B65630(a1, a2: 0xFFFFFFFFLL);
  if ( (_DWORD)result == 0 )
    sub_4B69760(a1, a2: "no function environment for tail call at level %d", v6);
```
sub_4B69390 - luaL_argerrorL
sub_4B69760 - luaL_errorL
