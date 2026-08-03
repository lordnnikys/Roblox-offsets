```lua_createtable, lua_setmetatable, lua_pushstring, lua_pushvalue, lua_settable, lua_replace```

lua_createtable - Creates a new Lua table and pushes it onto the stack.
lua_setmetatable    - Sets the metatable of a table (with `__metatable` lock check).
lua_pushstring - Pushes a C string onto the Lua stack.
lua_pushvalue - Pushes a copy of the value at a given stack index.
lua_settable - Performs t[key] = value.
lua_replace    - Replaces the value at a given index with the top stack value.

**IMPORTANT NOTICE** The addresses shown in the decompilation are the internal Luau functions that Roblox calls directly. Other dumps may list slightly different addresses for the same operation (e.g., lua_pushstring vs lua_pushlstring). Both work; the internal ones are just the raw building blocks, while the public ones are convenient wrappers. You can use either—the important thing is that they do the same thing under the hood.
These **ARE** harder to use than you will find in other dumps. Not recommended to use, but easy to find.

So, from previous guide which is Lua_SandBoxThread we saw:

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

And as you can see, there are multiple rva's to something, and these are

```lua_createtable
lua_setmetatable
lua_pushstring
lua_pushvalue
lua_settable
lua_replace```

Easy as that. There won't be example of use.
