# GetLuaStateForInstance
# AttachRobloxExtraSpace
# lua_setfield

All of them are pretty self explanatory.
I will make 2 separate guides by decompiling and without it, this one is without decompining.
To dump these offsets, it wont be THAT easy but you'll get it. Search for string (shift f12) "Script Start", you will land here:

```c
.rdata:000000000603AC80 aScriptStart    db 'Script Start',0     ; DATA XREF: sub_1DB7A80:loc_1DB7E6E↑o
```

Go by **second** xref. Now, there are 2 paths for GetLuaStateForInstance, you can either scroll up till you see loc_RVA (depends on roblox version):

```c
.text:0000000001DB7E0F loc_1DB7E0F:                            ; CODE XREF: sub_1DB7A80+389↑j
.text:0000000001DB7E0F                 movaps  xmm0, [rsp+440h+var_3F0]
.text:0000000001DB7E14                 movdqa  [rbp+340h+var_360], xmm0
.text:0000000001DB7E19                 lea     r8, [rbp+340h+var_360]
.text:0000000001DB7E1D                 lea     rdx, [rbp+340h+var_3C0]
.text:0000000001DB7E21                 call    sub_1D56360
```
 and first call you see after in my case **loc_1DB7E0F** will be GetLuaStateForInstance, so in my case it will be sub_1D56360 which is 0x1D56360
Then come back to "Script Start", there scroll down until next loc_RVA (depends on roblox version):

```c
.text:0000000001DB7EC5 loc_1DB7EC5:                            ; CODE XREF: sub_1DB7A80+43A↑j
.text:0000000001DB7EC5                 movaps  xmm6, [rsp+440h+var_3F0]
.text:0000000001DB7ECA                 movaps  [rbp+340h+var_350], xmm6
.text:0000000001DB7ECE                 lea     r9, [rbp+340h+var_1D0]
.text:                                 lea     rdx, [rbp+340h+var_3C0]
.text:0000000001DB7EE0                 call    sub_1DB73E0
```
 First call you see - AttachRobloxExtraSpace, so in my case its 0x1DB73E0

lua_setfield is on string "plugin" scroll up 2x loc_rva and you'll see call  sub_4B64870 after second loc, has to be done bottom to up. ~35 lines from "plugin" string if you're confused.
