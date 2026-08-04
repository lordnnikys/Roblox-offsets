```c++
#define CLOSURE_CONT_ENC vmval2
#define CLOSURE_DEBUGNAME_DEPRECATED_ENC vmval1
#define LSTATE_STACKSIZE_ENC vmval4
#define PROTO_ABSLINEINFO_ENC vmval3
#define PROTO_DEBUGINSN_ENC vmval2
#define PROTO_DEBUGNAME_ENC vmval1
#define PROTO_LINEINFO_ENC vmval3
#define PROTO_LOCVARS_ENC vmval1
#define PROTO_SOURCE_ENC vmval4
#define PROTO_TYPEINFO_ENC vmval3
#define PROTO_UPVALUES_ENC vmval2
#define PROTO_USERDATA_ENC vmval3
#define TSTRING_HASH_ENC vmval2
#define UDATA_META_ENC vmval2
```
```c++
uint64_t vmval1 = (uint64_t)(G + 0x4E0);  // ptrenckey[0]
uint64_t vmval2 = (uint64_t)(G + 0x4E8);  // ptrenckey[1]
uint64_t vmval3 = (uint64_t)(G + 0x4F0);  // ptrenckey[2]
uint64_t vmval4 = (uint64_t)(G + 0x4F8);  // ptrenckey[3]
```
```c++
vmval1 Proto->debugname, locvars, Closure->debugname `value = stored + addr`
vmval2 Proto->upvalues, debuginsn, TString->hash, Udata->metatable, Closure->cont `value = addr - stored`
vmval3 Proto->userdata, lineinfo, abslineinfo, typeinfo `value = stored ^ addr`
vmval4 Proto->source, L->stacksize `value = stored - addr`
```
