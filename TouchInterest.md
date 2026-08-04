# TouchInterest

**IMPORTANT NOTICE** - this is NOT FireTouchInterest, this is completely different offset that does completely different thing.
TouchInterest - property on BasePart that controls whether the part generates Touched events. Setting it to 1 forces a part to become "touchable", even if it normally wouldnt fire touch events.

To get TouchInterest search string "TouchInterest", select first (and only) xref:
```c
.rdata:00000000061D2ED0 aTouchinterest  db 'TouchInterest',0    ; DATA XREF: sub_2A21B20+D↑o // <-- TouchInterest
```
You can already stop there but if you want go to it, and decompile:
```c
_QWORD *__fastcall sub_2A21B20(_QWORD *a1, __int64 a2) // <-- TouchInterest
{
  __int64 v3; // rax
```

So the offset is 0x2A21B20
Example of use:
```c++
*(bool*)(part + TouchInterestOffset) = true;
```
```c++
*(bool*)(part + TouchInterestOffset) = false;
```
