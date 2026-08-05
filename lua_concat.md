# lua_concat

Search for string "level must be non-negative" select first or 3rd xref:
```c
  result = (_OWORD *)sub_4B65630(a1, a2: 0xFFFFFFFFLL);
  if ( (_DWORD)result == 0 )
    sub_4B69760(a1, a2: "no function environment for tail call at level %d", v6);
  return result;
}
```
Doble click sub_4B69760:
```c
void __noreturn sub_4B69760(__int64 a1, const char *a2, ...)
{
  va_list va; // [rsp+50h] [rbp+18h] BYREF

  va_start(va, a2);
  sub_4B6A7A0(a1, a2: 1);
  sub_4B638B0(a1, (__int64)a2, a3: (__int64)va);
  sub_4B61C30(a1, a2: 2); // <-- lua_concat
  sub_4B61F50(a1);
}
```

So the offset is 0x4B61C30
