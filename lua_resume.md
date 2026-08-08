# lua_resume

Resumes a suspended coroutine. Needed to actually run code in threads you create with lua_newthread.

Search string (shift+f12) `"cannot resume non-suspended coroutine"` go to **first** xref, decompile (f5):

```c
  v2 = *(a1 + 3);
  if ( v2 != 1 && v2 != 6 && (v2 != 0 || *(a1 + 72) != *(a1 + 96)) )
  {
    v4 = "cannot resume non-suspended coroutine";
    goto LABEL_9;
  }
```

That is `sub_948D40` - lua_resume.

Offset: **0x948D40**

```c++
int result = ((int(*)(lua_State*, lua_State*))REBASE(0x948D40))(L, coroutine);
```

Since first xref can be unreliable across updates, just visually inspect the code:
```c
__int64 __fastcall sub_948D40(__int64 a1, __int64 a2, int a3)
{
  char v3; // al
  unsigned __int16 v6; // ax
  __int16 v7; // ax
  char v8; // al
  __int64 v9; // rcx

  v3 = *(_BYTE *)(a1 + 3);
  if ( v3 != 1 && v3 != 6 && (v3 != 0 || *(_QWORD *)(a1 + 88) != *(_QWORD *)(a1 + 24)) )
    return sub_9485A0(a1, a2: "cannot resume non-suspended coroutine", a3);
  if ( a2 != 0 )
  {
    v6 = *(_WORD *)(a2 + 48);
    *(_WORD *)(a1 + 48) = v6;
    if ( v6 >= 0xC8u )
      return sub_9485A0(a1, a2: "C stack overflow", a3);
  }
  else
  {
    v6 = 0;
    *(_WORD *)(a1 + 48) = 0;
  }
  v7 = v6 + 1;
  *(_BYTE *)(a1 + 5) = 1;
  *(_WORD *)(a1 + 48) = v7;
  *(_WORD *)(a1 + 50) = v7;
  v8 = *(_BYTE *)(a1 + 1);
  if ( (v8 & 4) != 0 )
  {
    v9 = *(_QWORD *)(a1 + 112);
    *(_BYTE *)(a1 + 1) = v8 & 0xFB;
    *(_QWORD *)(a1 + 56) = *(_QWORD *)(v9 + 64);
    *(_QWORD *)(v9 + 64) = a1;
  }
  return 0;
}
```
Should look like this
