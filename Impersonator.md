# Impersonator

To get Impersonator search string "Callbacks cannot yield", go to xref and decompile it:
```c
sub_1E21510(a1: v24 + 2000, a2: (__int64)&v53, a3: (__int64)&v43, a4: v22, a5: 0, a6: nullptr);
  if ( v53 == 1 )
  {
    sub_1D3D8E0(a1: v41);
    sub_5154200(a1: "Callbacks cannot yield");
  }
  if ( v53 == 2 )
  {
    sub_1D3D8E0(a1: v41);
    v38 = sub_1D22AE0(a1: v19, a2: 0xFFFFFFFFLL);
    sub_6400A0(a1: v66, a2: v38);
    sub_643DA0(a1: pExceptionObject, a2: v66);
    CxxThrowException(pExceptionObject, pThrowInfo: (_ThrowInfo *)&_TI2_AVruntime_error_std__);
  }
  v25 = (int)(1 - v21 + sub_4B625F0(a1: (__int64)v19));
  v26 = (const char *)a5[1];
  v42 = v26;
  v27 = *a5;
  v28 = &v26[-*a5];
```
Double click the sub_1E21510 and find:
```c
LABEL_50:
    if ( *(_QWORD *)a3 != 0 )
      v25 = *(_QWORD *)(*(_QWORD *)a3 + 40LL);
    else
      v25 = 0;
    sub_1D52C40(a1: v67, a2: IdentityStruct, a3: v25);
    v63[0] = &v48;
    v63[1] = a1;
    v63[2] = &v43;
    v63[3] = &v44;
    v63[4] = &v45;
```

Double click sub_1D52C40:

```c
__int64 __fastcall sub_1D52C40(__int64 a1, int a2, __int64 a3)
{
  __int64 v6; // rax
  __int64 v7; // rbx
  int v8; // eax
  _BYTE v10[40]; // [rsp+30h] [rbp-28h] BYREF

  if ( a3 != 0 )
    v6 = sub_6D9F90(a1: a3);
  else
    v6 = 0;
  v7 = *(_QWORD *)(v6 + 144);
  v8 = sub_1D66AC0(a1: (__int64)v10, a2: a3);
  sub_4C2CA90(a1, a2, a3: v8, a4: v7, a5: a3); // <-- Impersonator
  return a1;
}
```

So the offset is 0x4C2CA90
