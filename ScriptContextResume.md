# ScriptContextResume

To get ScriptContextResume search string "[FLog::ScriptContext] Resuming script: %p", it has one xref which is the offset of ScriptContextResume: 

```c
.rdata:00000000060431A0 aFlogScriptcont_3 db '[FLog::ScriptContext] Resuming script: %p',0
.rdata:00000000060431A0                                         ; DATA XREF: sub_1E1E380+1EF↑o // <-- ScriptContextResume (sub_1E1E380)
``` 
obviously you can press that xref: 
```c
__int64 __fastcall sub_1E1E380(__int64 **a1)
```

So the offset is 0x1E1E380
