# FireServer
# FireClient

To find FireClient search for string "FireClient can only be called from the server" first xref, decompile:
```c
int __fastcall sub_274E730(__int64 a1, _QWORD *a2, _QWORD *a3, __int64 a4)
``` 
FireClient - 0x274E730

To find FireServer search for string "FireServer can only be called from the client" first xref, decompile: 
```c
__int64 __fastcall sub_274EAF0(__int64 a1, _QWORD *a2, __int64 a3)
{
```
FireServer - 0x274EAF0
