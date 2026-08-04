# SetFFlag

SetFFlag - sets engine fast flags.

To get SetFFlag search string "[FLog::FastLogValueChanged] Setting variable {}", first (and the only) xref:
```c
.rdata:0000000006C7CCF0 aFlogFastlogval db '[FLog::FastLogValueChanged] Setting variable {}',0
.rdata:0000000006C7CCF0                                         ; DATA XREF: sub_5172100+29A↑o //<-- SetFFlag
```
Or decompile:
```c
BOOL8 __fastcall sub_5172100(__int64 a1, __int128 *a2, _QWORD *a3, unsigned int a4, int a5, char a6)
{
```

So the offset is 0x5172100

Example of use:
```c++
((void(*)(const char*, bool))REBASE(0x5172100))("FFlag", true);
```
