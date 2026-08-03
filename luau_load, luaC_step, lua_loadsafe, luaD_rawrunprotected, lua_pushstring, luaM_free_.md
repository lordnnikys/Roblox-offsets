# luau_load
# luaC_step
# lua_loadsafe
# luaD_rawrunprotected
# lua_pushstring
# `luaM_free_`

Used to execute stuff... yup

To find it search string (shift f12) "not enough memory" and do **FOURTH** xref (use ctrl x if you dont see it), here you'll be put on 
```c
.text:0000000004B6EADB                 lea     rax, aNotEnoughMemor ; "not enough memory"
```
scroll up, until you see loc_RVA and some xref, press on that xref once and decompile:
```c
__int64 __fastcall sub_4B6EA30(__int64 a1, __int64 a2, __int64 a3, __int64 a4, int a5)
```
its ~50 lines but all we need is just first line, and as we can see luau_load is 0x4B6EA30.

To find luaC_step you need to just find this block:
```c
  {
    LOBYTE(a2) = 1;
    sub_4B6CD20(a1, a2);
    v9 = *(__int64 **)(a1 + 40);
    v10 = *v9;
  }
``` 

and well luaC_step is sub_4B6CD20 which is 0x4B6CD20

To get lua_loadsafe and luaD_rawrunprotected just locate this line
```c
  if ( (unsigned int)sub_4B68050(a1, a2: sub_4B6ECE0, a3: &v13) == 4 )
```
sub_4B68050 - luaD_rawrunprotected and sub_4B6ECE0 lua_loadsafe 

lua_pushstring can be found here:

```c
  {
    sub_4B63510(a1, a2: "not enough memory");
    v11 = 1;
  }
```
sub_4B63510 - lua_pushstring 

And finally `luaM_free_` can be found there:

```c
    sub_4B8A1A0(a1: v15, a2: v16, a3: 8 * v17, a4: 0);
  if ( *((_QWORD *)&v13 + 1) != 0 )
    sub_4B8A1A0(a1: v13, a2: *((_QWORD *)&v13 + 1), a3: 8 * v14, a4: 0);
```
and sub_4B8A1A0 is the offset
