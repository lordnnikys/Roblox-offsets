# luaS_newlstr

To find it search string (shift f12) "not enough memory", **third** xref decompile code and you'll be put here:

```c
  v13 = (_BYTE *)sub_4B9AB60(a1, a2: "not enough memory");
```
That is your luaS_newlstr
