# luaF_newCclosure

To dump luaF_newCclosure search string "_VERSION", go to its xref and decompile:
```c
__int64 __fastcall sub_4B7E520(_QWORD *a1)
{
  sub_4B63740(a1, a2: -10002);
  sub_4B64870(a1, a2: 4294957294LL, a3: &off_603A3C8);
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0);
  sub_4B63370((__int64)a1, a2: (__int64)"Luau");
  sub_4B64870(a1, a2: 4294957294LL, a3: "_VERSION");
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7E280, a3: 0, a4: 0, a5: 0); // <-- double click
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7E2F0, a3: (unsigned int)"ipairs", a4: 1, a5: 0);
```
Double click string that is under "_VERSION" so in my case sub_4B63030:
```c
  {
    sub_4B99F50(a1, a2: "stack overflow");
    sub_4B61F50(a1);
  }
  v9 = *(_QWORD *)(a1 + 72);
  if ( v9 == *(_QWORD *)(a1 + 96) )
    v10 = *(_QWORD *)(a1 + 120);
  else
    v10 = *(_QWORD *)(**(_QWORD **)(v9 + 16) + 16LL);
  v11 = (_QWORD *)sub_4B93CE0(a1, a2: v6, a3: v10); // <-- luaF_newCclosure
  v12 = v11;
  v11[5] = a2;
  v11[6] = (char *)v11 - a5 + 48;
```
And there under "stack overflow" next RVA after is is our luaF_newCclosure
So the offset is 0x4B93CE0
