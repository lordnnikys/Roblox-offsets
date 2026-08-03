# luaB offsets

This will be little unusual because it'll cover like 10 offsets. But anyways, to find luaB offsets search string "_VERSION" go to the only xref and decompile code:
There you will see this line (3rd line in the table)
```c
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);
```
double click off_6BBE0A0 and you'll be put to table with luaB offsets!
```c
.rdata:0000000006BBE0A0 off_6BBE0A0     dq offset aAssert       ; DATA XREF: sub_4B7E520+2B↑o
.rdata:0000000006BBE0A0                                         ; "assert"
.rdata:0000000006BBE0A8                 dq offset sub_4B7DF90
.rdata:0000000006BBE0B0                 dq offset aError_1      ; "error"
.rdata:0000000006BBE0B8                 dq offset sub_4B7DA50
```
luaB_assert is 0x4B7DF90
luaB_error is 0x4B7DA50 etc...

FULL LIST LOOKS LIKE THIS:
```c
.rdata:0000000006BBE0A0 off_6BBE0A0     dq offset aAssert       ; DATA XREF: sub_4B7E520+2B↑o
.rdata:0000000006BBE0A0                                         ; "assert"
.rdata:0000000006BBE0A8                 dq offset sub_4B7DF90
.rdata:0000000006BBE0B0                 dq offset aError_1      ; "error"
.rdata:0000000006BBE0B8                 dq offset sub_4B7DA50
.rdata:0000000006BBE0C0                 dq offset aGcinfo       ; "gcinfo"
.rdata:0000000006BBE0C8                 dq offset sub_4B7DE80
.rdata:0000000006BBE0D0                 dq offset aGetfenv      ; "getfenv"
.rdata:0000000006BBE0D8                 dq offset sub_4B7DBE0
.rdata:0000000006BBE0E0                 dq offset aGetmetatable ; "getmetatable"
.rdata:0000000006BBE0E8                 dq offset sub_4B7DAC0
.rdata:0000000006BBE0F0                 dq offset aNext_4       ; "next"
.rdata:0000000006BBE0F8                 dq offset sub_4B7DF30
.rdata:0000000006BBE100                 dq offset aNewproxy     ; "newproxy"
.rdata:0000000006BBE108                 dq offset sub_4B7E0E0
.rdata:0000000006BBE110                 dq offset aPrint        ; "print"
.rdata:0000000006BBE118                 dq offset sub_4B7D830
.rdata:0000000006BBE120                 dq offset aRawequal     ; "rawequal"
.rdata:0000000006BBE128                 dq offset sub_4B7DD20
.rdata:0000000006BBE130                 dq offset aRawget       ; "rawget"
.rdata:0000000006BBE138                 dq offset sub_4B7DD70
.rdata:0000000006BBE140                 dq offset aRawset       ; "rawset"
.rdata:0000000006BBE148                 dq offset sub_4B7DDC0
.rdata:0000000006BBE150                 dq offset aRawlen       ; "rawlen"
.rdata:0000000006BBE158                 dq offset sub_4B7DE20
.rdata:0000000006BBE160                 dq offset aSelect_1     ; "select"
.rdata:0000000006BBE168                 dq offset sub_4B7E000
.rdata:0000000006BBE170                 dq offset aSetfenv      ; "setfenv"
.rdata:0000000006BBE178                 dq offset sub_4B7DC40
.rdata:0000000006BBE180                 dq offset aSetmetatable ; "setmetatable"
.rdata:0000000006BBE188                 dq offset sub_4B7DB20
.rdata:0000000006BBE190                 dq offset aTonumber     ; "tonumber"
.rdata:0000000006BBE198                 dq offset sub_4B7D910
.rdata:0000000006BBE1A0                 dq offset aTostring     ; "tostring"
```
