# raknetrecieve

Search for string `"[DFLog::NetworkTrace] Incoming packet error: length <= 2 || buffer == 0, length=%d, address=%s"`
and the only xref is the offset:
```c
.rdata:00000000062C3DF0 aDflogNetworktr_14 db '[DFLog::NetworkTrace] Incoming packet error: length <= 2 || buffe'
.rdata:00000000062C3DF0                                         ; DATA XREF: sub_32626B0+1F0B↑o // <-- raknetrecieve
```

So the offset is 0x32626B0
