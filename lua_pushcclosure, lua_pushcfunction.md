# lua_pushcclosure
# lua_pushcfunction

To get lua_pushcfunction we'll need help from lua_newthread offset which in my case is 0x4B62BD0. Jump to 0x4B62BD0 and scroll down until you find SUBROUTINE it is it:
```c
text:0000000004B62CA0 ; =============== S U B R O U T I N E =======================================
.text:0000000004B62CA0
.text:0000000004B62CA0
.text:0000000004B62CA0 ; __int64 __fastcall sub_4B62CA0(__int64, __int64, unsigned int) // <-- lua_pushcfunction
.text:0000000004B62CA0 sub_4B62CA0     proc near               ; CODE XREF: sub_4B7E0E0+39↓p
.text:0000000004B62CA0
.text:0000000004B62CA0 arg_0           = qword ptr  8
.text:0000000004B62CA0 arg_8           = qword ptr  10h

```

So the offset is 0x4B62CA0 for lua_pushfunction

Example of use:
```c++
((void(*)(lua_State*, lua_CFunction, int))REBASE(0x4B62CA0))(L, myFunc, 0);
```

To get lua_pushcclosure we'll need help from lua_newthread offset which in my case is 0x4B62BD0. Jump to 0x4B62BD0 and scroll down until you find SUBROUTINE which is AFTER  sub_4B62CA0 so second subroutine it is it:
```c
.text:0000000004B62D60 ; =============== S U B R O U T I N E =======================================
.text:0000000004B62D60
.text:0000000004B62D60
.text:0000000004B62D60 ; __int64 __fastcall sub_4B62D60(__int64, __int64, int) // <-- lua_pushcclosure
.text:0000000004B62D60 sub_4B62D60     proc near               ; CODE XREF: sub_1D225E0+6↑j
.text:0000000004B62D60
.text:0000000004B62D60 arg_0           = qword ptr  8
.text:0000000004B62D60 arg_8           = qword ptr  10h
```

So the offset is 0x4B62D60
Example of use:
```c++
((void(*)(lua_State*, lua_CFunction, int))REBASE(0x4B62D60))(L, myClosure, 1);
```
