# Lua_SandBoxThread

Used for activating the sandbox on a new Lua thread, allowing the thread to run scripts with the correct identity and permissions.

To dump Lua_SandBoxThread you need to find string (shift f12 in ida, "s" in ghidra) " `"__index"` just that, nothing else. Go to **second** xref, that is your Lua_SandBoxThread.


`.text:0000000001DA9DC3                 lea     rdx, aIndex_1   ; "__index"`

There's really no need to decompile it, but if you want to be completely sure, press f5 (decompile) on it

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
}```

sub_1DA9D90 - Lua_SandBoxThread

So the offset is 0x1DA9D90

Example of use:

```c++
lua_State* thread = lua_newthread(mainL);
((void(*)(lua_State*))REBASE(0x1DA9D90))(thread);   // activate sandbox```
