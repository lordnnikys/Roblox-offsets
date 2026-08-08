# Require Bypass

Used for disabling roblox's security against require() calls.

To dump require bypass you find string (shift f12 in ida, "s" in ghidra) "Cannot require a non-RobloxScript" go to **second** xref and decompile it (f5), after which you will be in my case `sub_2334770` where you will see error messages for require security. You will find:

```c
        if ( *(_BYTE *)(v29 + 2112) == 0 ) // <-- require bypass
        {
          v30 = *(_QWORD *)(a1 + 32);
          v156 = *(_OWORD *)(v30 + 48);
          v157 = *(_QWORD *)(v30 + 64);
          if ( (sub_8EB520(a1: &v156) & 8) != 0 )
          {
            if ( (*(_BYTE *)(v132 + 360) & 1) == 0 )
            {
              __eh34_enter_wind_state(1, 8);
              sub_2C9D040(a1: "Cannot require a non-RobloxScript module from a RobloxScript"); // <-- you'll be put here
```

The byte at offset +2112 (+0x840) from `v29` controls whether the require security check fires. When this byte is `0`, the check runs. When it's `1`, it **skips** all the security logic below it.

`v29` is resolved through:
```
v29 = *(*(*(ScriptContext + 0x20) + 0x18) + 0x10)
```

Offset can be both 0x840 and 0x9D0

Which works out to: the byte at **ScriptContext + 0x9D0** controls require bypass.

Offset: **0x9D0**

Usage:
```c
*(unsigned char*)(scriptContext + 0x9D0) = 1; // 1 = disable require checks
```
