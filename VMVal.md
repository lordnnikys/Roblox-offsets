uint64_t vmval1 = (uint64_t)(G + 0x4E0);  // ptrenckey[0]
uint64_t vmval2 = (uint64_t)(G + 0x4E8);  // ptrenckey[1]
uint64_t vmval3 = (uint64_t)(G + 0x4F0);  // ptrenckey[2]
uint64_t vmval4 = (uint64_t)(G + 0x4F8);  // ptrenckey[3]

vmval1 Proto->debugname, locvars, Closure->debugname | `value = stored + addr` |
vmval2 Proto->upvalues, debuginsn, TString->hash, Udata->metatable, Closure->cont | `value = addr - stored` |
vmval3 Proto->userdata, lineinfo, abslineinfo, typeinfo | `value = stored ^ addr` |
vmval4 Proto->source, L->stacksize | `value = stored - addr` |
