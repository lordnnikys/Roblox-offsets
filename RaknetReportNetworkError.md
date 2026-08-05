# RaknetReportNetworkError

Search for string "ConnectionFailure" or "reportPerServerMetric" and there will be 1 xref:
```c
.rdata:0000000005EB48C8 aConnectionfail db 'ConnectionFailure',0
.rdata:0000000005EB48C8                                         ; DATA XREF: sub_A3DEA0+21E↑o
```
```c
.rdata:0000000005EB6770 aDflogNetworktr db '[DFLog::NetworkTrace] reportPerServerMetric::: sc(%s:%d).state = '
.rdata:0000000005EB6770                                         ; DATA XREF: sub_A3DEA0+74C↑o
```

So the offset is 0xA3DEA0
