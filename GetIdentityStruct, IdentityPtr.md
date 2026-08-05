# GetIdentityStruct
# IdentityPtr

Used to give your thread identity

To find them both you need to press alt b (byte search) and search for `55 56 57 53 48 83 EC 28 48 8D 6C 24 ? 48 89 CF` you will be put to in my case
```c
.text:00000000000080E0 sub_80E0        proc near               ; CODE XREF: GetIdentityStruct_Thunk↓j
```
you need to press xref **once** and press x, search for "GetIdentityStruct+7 jmp GetIdentityStruct_Thunk" double click it, and go 1 line upwards, this is GetIdentityStruct:

```c
.text:0000000004C2CE10                 mov     rcx, cs:g_pIdentityStruct <-- your offset
.text:0000000004C2CE17                 jmp     GetIdentityStruct_Thunk <-- currently you're here
```

And to get IdentityPtr you just do 0x4C2CE10 + 7 + 0x03765D11 = 0x8392B28 (RIP math I am funny asf) now get 0x03765D11 mov     rcx, cs:g read these, convert to bytes at offset +3 (in OUR case 11 5D 76 03) and reverse to number. Just ask ai💀💀 to do it give it GetIdentityStruct + 7 + 0x03765D11
