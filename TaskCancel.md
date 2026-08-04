# TaskCancel

TaskCancel - cancels next scheduled task.

To get TaskCancel search string "cannot cancel thread", first (and the only) xref:
```c
.rdata:000000000604A4E8 aCannotCancelTh db 'cannot cancel thread',0
.rdata:000000000604A4E8                                         ; DATA XREF: sub_1E95330:loc_1E953C0↑o // <-- xref is TaskCancel
```
So we can see that offset is 0x1E95330, if you want to decompile:
```c
__int64 __fastcall sub_1E95330(__int64 a1) // <-- TaskCancel
{
  __int64 v2; // rax
  __int64 v3; // rbx
  int v4; // eax

  v2 = sub_4B653F0(a1, a2: 1);
  v3 = v2;
  if ( v2 == 0 )
    sub_4B6A680(a1, a2: 1, a3: "thread");
  if ( v2 == a1 || (v4 = sub_3E0C730(a1: v2)) != 1 && (v4 == 6 || v4 == 0 && (unsigned int)sub_4B6BF40(a1: v3) != 0) )
    sub_4B69760(a1, a2: "cannot cancel thread");
  *(_BYTE *)(sub_6D9F90(a1: v3) + 164) = 0;
  sub_4B67390(a1: v3);
  return 0;
}
```

So the offset is 0x1E95330

Example of use:
```c++
((void(*)(int))REBASE(0x1E95330))(taskHandle);
```
