# RaknetSend

Search for string "[FLog::Network] out of memory in raknet at callsite %ld" and first xref will be it:
```c
.rdata:00000000062C3470 aFlogNetworkOut db '[FLog::Network] out of memory in raknet at callsite %ld',0
.rdata:00000000062C3470                                         ; DATA XREF: sub_324EE80+9B↑o
.rdata:00000000062C3470                                         ; sub_3255930+1A↑o
```

So the offset is 0x324EE80
