# lua_encodepointer

Encodes/encrypts a pointer field for storage. Used by all Luau structs to obfuscate internal pointers.

Not a standalone function in this build - the encoding is inlined as VMValue operations:

```c
// SET operations (encode for storage):
// VMValue1: data = value + (data + offset)        // ADD  - ADD32_MEM encode
// VMValue2: data = (data + offset) - value         // SUB  - SUB32_MEM encode
// VMValue3: data = value ^ (data + offset)         // XOR  - XOR32_MEM encode

// GET operations (decode for use):
// VMValue1: (data + offset) = data - value
// VMValue2: (data + offset) = data + value
// VMValue3: (data + offset) = data ^ value
```

Examples from the bytecode loader (sub_97C200):
- Proto->bytecode: XOR encoded (VMValue3)
- TString->hash: SUB encoded (VMValue2)
- Closure->upvals: ADD encoded (VMValue1)

The key is the field address itself (pointer + offset), making each encoding field-unique without a stored key.
