# lua_tothread

To find lua_tothread we'll use already known offset TaskCancel which in my case is at 0x1E95330 jump to it, decompile and find:
```c
  __int64 v3; // rbx
  int v4; // eax

  v2 = sub_4B653F0(a1, a2: 1); // <-- lua_tothread
  v3 = v2;
  if ( v2 == 0 )
    sub_4B6A680(a1, a2: 1, a3: "thread");
```

So the offset is 0x4B653F0
