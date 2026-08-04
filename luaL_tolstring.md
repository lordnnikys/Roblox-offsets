# luaL_tolstring 


This will be dumped with the help of luaB offsets we found (search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);)

So. to get luaL_tolstring  locate:
```c
.rdata:0000000006BBE110                 dq offset aPrint        ; "print"
.rdata:0000000006BBE118                 dq offset sub_4B7D830
```
Double click the sub_RVA and decompile:
```c
    {
      v4 = sub_4B69F70(a1, a2: v2, a3: &v10); // <-- luaL_tolstring 
      if ( v2 > 1 )
      {
```
