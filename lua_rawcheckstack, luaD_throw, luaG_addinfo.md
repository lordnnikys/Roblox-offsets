# lua_rawcheckstack 
# luaD_throw 
# luaG_addinfo 

lua_rawcheckstack - makes sure that the Lua stack has enough space for new values. Used internally before pushing error messages.
luaD_throw - Performs the actual stack unwinding when a Lua error is thrown. This is the final step that stops script execution.
luaG_addinfo Adds source file name and line number to an error message ("scirpt.lua:5: attempt to call nil a value."). Called by luaG_runerrorL before throwing.

In previous guide we found LuaG_runerror, from it we can actually find lua_rawcheckstack, luaD_throw, luaG_addinfo:

```c
__int64 __fastcall sub_1DA9D90(__int64 a1)
{
  sub_4B61D80(a1, a2: 0, a3: 0);
  sub_4B61D80(a1, a2: 0, a3: 0);
  sub_1D22700(a1, a2: 0xFFFFFFFFLL);
  sub_4B63370(a1, a2: "__index", a3: 7);
  sub_4B63740(a1, a2: 4294957294LL);
  sub_4B64B40(a1, a2: 4294967293LL);
  return sub_4B64920(a1, a2: 4294967294LL);
}
```

double click **sub_4B64920**

Find:
```c
    if ( *(_BYTE *)(*(_QWORD *)v4 + 4LL) != 0 )
      sub_4B6B440(a1);
    *(_QWORD *)(*(_QWORD *)v4 + 16LL) = v5;
  }``` (value of sub_4B6B440 will be different depending on your version)

```c
void __fastcall __noreturn sub_4B6B440(__int64 a1)
{
  sub_4B6B470(a1, a2: "attempt to modify a readonly table");
}
```

sub_4B6B470 - luaG_runerror, double click it:

```c
void __noreturn sub_4B6B470(__int64 a1, char *a2, ...)
{
  char Buffer[520]; // [rsp+20h] [rbp-208h] BYREF
  va_list va; // [rsp+240h] [rbp+18h] BYREF

  va_start(va, a2);
  sub_799C60(Buffer, BufferCount: 0x200u, Format: a2, ArgList: va);
  sub_4B63910(a1, a2: 1);
  sub_4B6BF70(a1, a2: Buffer);
  sub_4B68390(a1, a2: 2);
}
```

there you can see these, sub_799C60 is not a lua function, thats microsoft function to format the error string

sub_4B63910 - lua_rawcheckstack
sub_4B6BF70 - luaG_addinfo
sub_4B68390 - luaD_throw
