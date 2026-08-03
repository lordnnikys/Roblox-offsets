# lua_pushstring

lua_pushstring can be found by searching string `"'__tostring' must return a string"`, there is only 1 xref, go to it and decompile: 

```c
    goto LABEL_6;
  sub_4B63510(a1, a2: "__tostring"); // <-- lua_pushstring
  sub_4B63A40(a1, a2: 4294967294LL);
```

OR
```c
          v9 = dword_5E47990;
        sub_4B63510(a1, a2: v9); // <-- lua_pushstring
        break;
```

So the offset is 0x4B63510

Example of use:
```c++
((void(*)(lua_State*, const char*))REBASE(0x4B63510))(L, "Hello, World!");
```
