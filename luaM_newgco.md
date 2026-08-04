# luaM_newgco

To dump luaM_newgco we will use already known lua_createtable which in my case is sub_4B6CD20 go to it, decompile and find:
```c
    v6(a1, a2: 0);
  if ( *(_BYTE *)(v2 + 73) == 0 )
  {
    v8 = sub_4B89F90();
    v9 = *(_BYTE *)(v2 + 73);
    *(double *)(v2 + 18688) = v8;
    if ( v9 == 0 )
    {
      v10 = sub_4B89F90();
      *(double *)(v2 + 18992) = v10;
      *(double *)(v2 + 18984) = v10 - *(double *)(v2 + 18776);
    }
  }
  v11 = sub_4B89F90();
  if ( byte_7A36590 != 0 && a2 != 0 && v5 * *(int *)(v2 + 20) / 0x64 > v7 )
    v7 = v5 * *(int *)(v2 + 20) / 0x64;
  v12 = *(unsigned __int8 *)(v2 + 73);
  v13 = sub_4B6C800(a1, a2: v7); // <-- double click this
  v14 = sub_4B89F90() - v11;
  if ( v12 != 0 )
  {
    if ( v12 != 1 && v12 != 2 )
    {
      if ( v12 == 3 )
      {
        *(double *)(v2 + 19064) = v14 + *(double *)(v2 + 19064);
      }
      else if ( v12 == 4 )
```
Find sub_4B6C800 and double click it:
```c
          return sub_4B6C030(a1);
        case 4:
          if ( *(_QWORD *)(v2 + 96) != 0 )
          {
            while ( v4 < a2 )
            {
              v8 = __crt_win32_buffer_debug_info::file_name(this: *(__crt_win32_buffer_debug_info **)(v2 + 96));
              v4 += (int)(16 * sub_4B6DF60(a1, a2: *(_QWORD *)(v2 + 96)));
              *(_QWORD *)(v2 + 96) = v8;
              if ( v8 == nullptr )
                goto LABEL_9;
            }
          }
          else
          {
LABEL_9:          return sub_4B6C030(a1);
        case 4:
          if ( *(_QWORD *)(v2 + 96) != 0 )
          {
            while ( v4 < a2 )
            {
              v8 = __crt_win32_buffer_debug_info::file_name(this: *(__crt_win32_buffer_debug_info **)(v2 + 96));
              v4 += (int)(16 * sub_4B6DF60(a1, a2: *(_QWORD *)(v2 + 96))); // Double click
              *(_QWORD *)(v2 + 96) = v8;
              if ( v8 == nullptr )
                goto LABEL_9;
            }
          }
          else
          {
LABEL_9:
```
Double click sub_4B6DF60:
```c
      LODWORD(v4) = (_DWORD)v12;
      return (unsigned int)(((int)v9 - (int)v4) / v10);
    }
  }
  if ( ((*v4 ^ 3) & v7) != 0 )
  {
    *v4 = v6 | *v4 & 0xF8;
    goto LABEL_18;
  }
  switch ( v4[1] )
  {
    case 5u:
      sub_4B9A500(a1, a2: v4, a3: a2);
      break;
    case 6u:
      sub_4B9AA70(a1, a2: v4, a3: a2); // <-- double click this
      break;
    case 7u:
      sub_4B8C080(a1, a2: (__int64)v4, a3: a2);
      break;
    case 8u:
      sub_4B93A40(a1, a2: v4, a3: a2);
      break;
    case 9u:
      sub_4B9A3E0(a1, a2: v4, a3: a2);
```

Double click sub_4B9AA70:
```c
LABEL_10:
    *(_DWORD *)(*(_QWORD *)(a1 + 40) + 1232LL) &= ~0x20000000u;
  }
  return sub_4B8A220(a1, a2, a3: *(_DWORD *)(a2 + 20) + 25, a4: *(unsigned __int8 *)(a2 + 2), // <--luaM_newgco  a5: a3);
}
```

So the offset is 0x4B8A220
