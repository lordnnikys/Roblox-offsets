# lua_pushinteger

Pushes an integer onto the Lua stack. Like lua_pushnumber but for whole numbers (tag 2 instead of tag 3).

lua_pushinteger can be found above lua_pushnumber, we will take "stack overflow" as an anchor, lets take offset we already know (4B63510), so, lua_pushinteger will be located on 4th "stack overflow"

```c
.text:0000000004B63357 loc_4B63357:                            ; CODE XREF: sub_4B632F0+3F↑j
.text:0000000004B63357                 lea     rdx, aStackOverflow ; "stack overflow"
.text:0000000004B6335E                 mov     rcx, rbx
.text:0000000004B63361                 call    sub_4B99F50
.text:0000000004B63366                 mov     rcx, rbx
.text:0000000004B63369                 call    sub_4B61F50
.text:0000000004B63369 sub_4B632F0     endp // <-- lua_pushinteger
```

so the offset is sub_4B632F0 or 0x4B632F0

use example:
```c++
((void(*)(lua_State*, long long))REBASE(0x4B632F0))(L, 42);
```
