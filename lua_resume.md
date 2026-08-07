# lua_resume

Resumes a suspended coroutine. Needed to actually run code in threads you create with lua_newthread.

Search string (shift+f12) **"cannot resume non-suspended coroutine"** — go to its **first** xref decompile:
```c
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

So the offset is sub_4B68510 (0x4B68510)

Example of use: 
```c++
int result = ((int(*)(lua_State*, lua_State*))REBASE(0x4B68510))(L, coroutine);
```

Saying "first" xref can be unreliable, just visually check for it:
```c
__int64 __fastcall sub_948D40(__int64 a1, __int64 a2)
{
  char v2; // al
  unsigned __int16 v5; // ax
  __int16 v6; // ax
  char v7; // al
  __int64 v8; // rcx

  v2 = *(_BYTE *)(a1 + 3);
  if ( v2 != 1 && v2 != 6 && (v2 != 0 || *(_QWORD *)(a1 + 88) != *(_QWORD *)(a1 + 24)) )
    return sub_9485A0(a1, a2: "cannot resume non-suspended coroutine");
  if ( a2 != 0 )
  {
    v5 = *(_WORD *)(a2 + 48);
    *(_WORD *)(a1 + 48) = v5;
    if ( v5 >= 0xC8u )
      return sub_9485A0(a1, a2: "C stack overflow");
  }
  else
  {
    v5 = 0;
    *(_WORD *)(a1 + 48) = 0;
  }
  v6 = v5 + 1;
  *(_BYTE *)(a1 + 5) = 1;
  *(_WORD *)(a1 + 48) = v6;
  *(_WORD *)(a1 + 50) = v6;
  v7 = *(_BYTE *)(a1 + 1);
  if ( (v7 & 4) != 0 )
  {
    v8 = *(_QWORD *)(a1 + 112);
    *(_BYTE *)(a1 + 1) = v7 & 0xFB;
    *(_QWORD *)(a1 + 56) = *(_QWORD *)(v8 + 64);
    *(_QWORD *)(v8 + 64) = a1;
  }
  return 0;
}
```

Supposed to look like this.
