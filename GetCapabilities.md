# GetCapabilities

To get GetCapabilities we will use already known impersonator offset (sub_4C2CA90) decompile it:
```c
  *(_QWORD *)(a1 + 24) = *(_QWORD *)(a2 + 16);
  *(_QWORD *)(a1 + 32) = *(_QWORD *)(a2 + 40);
  *(_QWORD *)(a1 + 40) = *(_QWORD *)(a2 + 24);
  *(_BYTE *)(a1 + 48) = *(_BYTE *)(a2 + 32);
  v9 = sub_4C2D260(a1: (int *)a3); // <-- GetCapabilities
  v10 = *a3;
  v11 = *((double *)a3 + 2);
  *((_QWORD *)&v17 + 1) = a4 & 0xFFFFFFFFFFFFFF00uLL | v9;
  v12 = *(_BYTE *)(a2 + 32);
```
Well... Literally the only offset in sub_4C2CA90 you can't mess that up.
So the offset is 0x4C2D260
