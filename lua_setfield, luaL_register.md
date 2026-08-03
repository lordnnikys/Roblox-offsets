# lua_setfield
# luaL_register

lua_setfield, luaL_register can be found by searching string "_VERSION", there is only 1 xref, go to it and decompile: 
```c
__int64 __fastcall sub_4B7E520(_QWORD *a1)
{
  sub_4B63740(a1, a2: -10002);
  sub_4B64870(a1, a2: 4294957294LL, a3: &off_603A3C8); // <-- lua_setfield
  sub_4B69E30(a1, a2: &off_603A3C8, a3: &off_6BBE0A0); // <-- luaL_register
  sub_4B63370((__int64)a1, a2: (__int64)"Luau");
  sub_4B64870(a1, a2: 4294957294LL, a3: "_VERSION"); // <-- lua_setfield
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7E280, a3: 0, a4: 0, a5: 0);
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7E2F0, a3: (unsigned int)"ipairs", a4: 1, a5: 0);
  sub_4B64870(a1, a2: 4294967294LL, a3: "ipairs"); // <-- lua_setfield
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7DF30, a3: 0, a4: 0, a5: 0);
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7E340, a3: (unsigned int)"pairs", a4: 1, a5: 0);
  sub_4B64870(a1, a2: 4294967294LL, a3: "pairs"); // <-- lua_setfield
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7E400, a3: (unsigned int)"pcall", a4: 0, a5: (__int64)sub_4B7E390);
  sub_4B64870(a1, a2: 4294967294LL, a3: "pcall"); // <-- lua_setfield
  sub_4B63030((_DWORD)a1, a2: (unsigned int)sub_4B7E4B0, a3: (unsigned int)"xpcall", a4: 0, a5: (__int64)sub_4B7E440);
  sub_4B64870(a1, a2: 4294967294LL, a3: "xpcall"); // <-- lua_setfield 
  return 1;
}
```

lua_setfield - 0x4B64870
luaL_register - 0x4B69E30
