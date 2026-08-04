# Lua_pseudoaddr
# LuaO_nilobject
# luaC_barrierf 

Lua_pseudoaddr - used for converting a Lua stack index (like -1 or -10002) into a real memory address.
LuaO_nilobject  - A global “nil” placeholder that is returned when a stack slot is empty, instead of creating a new nil object every time.
luaC_barrierf -he garbage collector write barrier for functions. Makes sure objects that are still in use don’t get deleted early.

To dump Lua_pseudoaddr you do same stuff as Lua_SandBoxThread (`"__index"` string + second xref) but you have to decompile it (f5):
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
There, double click **sub_4B64920** and you'll see:

```c
    {
      v4 = (int *)sub_4B65A60();
      v3 = a1[7];
    }
```
That is Lua_pseudoaddr, so the offset is 0x4B65A60

Then if you look bit down:
 ```c
{
    v3 = a1[7];
    v4 = (int *)(16LL * a2 + a1[8] - 16LL);
    if ( (unsigned __int64)v4 >= v3 )
      v4 = (int *)&unk_6BC0438;
  }
```
LuaO_nilobject - unk_6BC0438 so the offset is 0x6bc0438

And if you scroll down a bit you will see: 

```c
  if ( v5 != nullptr && (**(_BYTE **)v4 & 4) != 0 && (*v5 & 3) != 0 )
    sub_4B6CAE0(a1, a2: *(_QWORD *)v4, a3: v5);
  a1[7] -= 16LL;
```
4B6CAE0 is your luaC_barrierf 

Also to mention there's luaG_readonlyerror
```c
    if ( *(_BYTE *)(*(_QWORD *)v4 + 4LL) != 0 )
      sub_4B6B440(a1);
    *(_QWORD *)(*(_QWORD *)v4 + 16LL) = v5;
  }
```
But it is completely useless.
