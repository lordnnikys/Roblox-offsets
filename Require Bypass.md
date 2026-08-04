# Require Bypass

Used for disabling roblox's security against require() calls.

To dump require bypass you find string (shift f12 in ida, "s" in ghidra) "Cannot require a non" go to **second** xref and decompile it (f5), after which you will be put here:

```c
 if ( (unsigned __int8)sub_1D55ED0(a1: v16) == 0 )
  {
    sub_1D66AC0(a1: v92, a2: a1);
    if ( (unsigned __int8)sub_4C2D610(a1: v92, a2: 8) != 0 && (unsigned __int8)sub_1DEA640(a1: v70) == 0 )
      sub_5154200(a1: "Cannot require a non-RobloxScript module from a RobloxScript");
    if ( (unsigned __int8)sub_4C2D610(a1: v92, a2: 8) == 0 && (unsigned __int8)sub_1DEA640(a1: v70) != 0 )
      sub_5154200(a1: "Cannot require a RobloxScript module from a non RobloxScript context");
  }
```
Double click **sub_1D55ED0** (or whatever value will be here on your Roblox version) and you will be put here:

```c
__int64 __fastcall sub_1D55ED0(__int64 a1)
{
  if ( *(int *)(a1 + 4792) >= 3 )
    sub_513AB80(a1: 0, a2: "Invalid Facet Access");
  return sub_1DABCC0(a1: a1 + 2048);
}
```
There you double click **sub_1DABCC0** (or once again whatever value will be here) and there will be:
```c
  return *(unsigned __int8 *)(a1 + 464);
```
All left to do is 2048+464 in hex, which will be 9d0

So the offset is 0x9d0

Offset example of use: ```*(unsigned char*)(scriptcontext + 0x9D0) = 1 <-- 1 - disable;```
