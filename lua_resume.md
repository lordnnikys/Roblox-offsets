# lua_resume

Resumes a suspended coroutine. Needed to actually run code in threads you create with lua_newthread.

Search string (shift+f12) **"cannot resume non-suspended coroutine"** — go to its **second** xref decompile:
```
   v2 = *(a1 + 3);
   if (v2 != 1 && v2 != 6 && (v2 != 0 || *(a1 + 72) != *(a1 + 96)))
   {
       v4 = "cannot resume non-suspended coroutine";
       goto LABEL_9;
   }
```
That function is lua_resume (thats just check that this is the correct function, actual offset is on first line: 
```c
__int64 __fastcall sub_4B68510(__int64 a1, __int64 a2)
```
