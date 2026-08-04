# luah_dummynode

To find luah_dummynode we'll use already known offset luah_new which is in my case 0x4B8C810, jump to it, decompile and find:
```c
  *(_QWORD *)(v6 + 8) = 0;
  *(_BYTE *)(v6 + 3) = 0;
  *(_QWORD *)(v6 + 24) = &unk_6BC02C8; // <-- luah_dummynode
  if ( (int)v4 > 0 )
  {
```

So the offset is 0x6BC02C8
