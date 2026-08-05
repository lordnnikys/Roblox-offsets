# luaH_getn

Use already known lua_objlen, in my case 0x4B62F20, jump to it and decompile:
```c
  switch ( v2[3] )
  {
    case 6:
      return *(unsigned int *)(*(_QWORD *)v2 + 20LL);
    case 7:
      return sub_4B8C4C0(a1: *(_QWORD *)v2); // <-- luaH_getn
    case 9:
    case 0xB:
      return *(unsigned int *)(*(_QWORD *)v2 + 4LL);
    default:
      break;
```

So the offset is 0x4B8C4C0
