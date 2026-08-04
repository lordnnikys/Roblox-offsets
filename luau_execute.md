# luau_execute

luau_execute - makes ur lua scripts actually run.

To find it search for already known offset (lua_resume) which in my case is sub_4B68510, decompile it,
and right at the end you'll see:
```c
    v10 = (unsigned int)sub_4B68050(a1, a2: (void (__fastcall *)(__int64, __int64))sub_4B68C00, a3: v9);
  }
  return sub_4B68B00(a1, a2: v10, a3: v12);
}
```
Double click that sub_4B68B00, and near the start find:
```c
  unsigned __int64 v12; // rcx

  for ( i = a2; i != 0; i = sub_4B68050(a1, a2: (void (__fastcall *)(__int64, __int64))sub_4B68C00, a3: v6) )
  {
    v6 = sub_4B68AD0(a1);
    if ( v6 == 0 )
```
Double click sub_4B68C00, find this near end:
```c
  if ( *(_BYTE *)(a1 + 3) == 0 )
  {
    sub_4B7B4A0(a1, a2: *(_QWORD *)(a1 + 56) - 16LL * (int)result);
    return sub_4B68810(a1);
  }
  return result;
}
```
Double click sub_4B68810, find:
```c
      if ( byte_7A36550 != 0 && (*(_BYTE *)(v3 + 44) & 8) != 0 )
        sub_4B7B440(a1);
      sub_4B7B430(a1); // <-- luau_execute!
    }
  }
```

So the offset is 0x4B7B430
