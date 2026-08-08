# lua_pushnumber

Pushes a double (floating point number) onto the Lua stack.

Binary search `5F 5F 69 6E 64 65 78 00` (`"__index"` in hex) - go to **second** xref (SandBoxThread). Decompile (f5), find the call that sets `__index` / `__newindex`:

```c
      if ( a3 != 0 )
      {
        v53 = 15;
        v52 = 7;
        strcpy((char *)v51, "__index"); // <-- you're put here 
        __eh34_enter_wind_state(-1, 1);
        v31 = v48;
        sub_119DE10(a1, a2: a3, a3: v51, a4: v48); // <-- double click this
        if ( __eh34_unwind(1) )
        {
unwind_state_1:
          sub_7B3D20(a1: v51);
```

Decompile `sub_119DE10`. Right at the top:

```c
  unsigned __int8 v71; // [rsp+A0h] [rbp+8h]

  v4 = a2;
  sub_938E80(a1, a2: a4); // <-- lua_pushnumber
  if ( *(_QWORD *)(*(_QWORD *)(a1 + 112) + 88LL) >= *(_QWORD *)(*(_QWORD *)(a1 + 112) + 80LL) )
  {
    LOBYTE(v7) = 1;
    sub_94BEC0(a1, a2: v7);
  }
```

Double click `sub_938E80`:

```c
__int64 __fastcall sub_938E80(__int64 a1, int a2)
{
  __int64 result; // rax

  if ( (unsigned __int64)(*(_QWORD *)(a1 + 72) + 16LL) > **(_QWORD **)(a1 + 88)
    && (unsigned int)sub_937DA0(a1, a2: 1) == 0 )
  {
    sub_977900(a1, a2: (__int64)"stack overflow");
    sub_93A2B0(a1);
  }
  result = *(_QWORD *)(a1 + 72);
  *(_DWORD *)(result + 12) = 3; // <-- lua_tnumber
  *(double *)result = (double)a2;
  *(_QWORD *)(a1 + 72) += 16LL;
  return result;
}
```

Offset: **0x938E80**

```c++
((void(*)(lua_State*, double))REBASE(0x938E80))(L, 42.0);
```
