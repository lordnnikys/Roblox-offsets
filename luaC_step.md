# luaC_step

luaC_step can be found by searching string "script start", thats scriptcontext, and find:
```c
          __eh34_enter_wind_state(6, 7);
          v29 = *(_QWORD *)(*(_QWORD *)(v27 + 24) + 40LL);
          v253 = v29;
          v254 = *(_QWORD *)(v29 + 312);
          *(_QWORD *)(v29 + 312) = "Script Start";
          if ( *(int *)(v28 + 4784) >= 3 )
          {
            v243 = "sor.png";
            sub_2C9AD80(a1: 0, a2: (__int64)&aTexturesCursor_5[-1021808]);
          }
          if ( __eh34_unwind(7) )
            goto unwind_state_7;
          __eh34_exit_wind_state(7, 6);
          __wind
          {
            *(_QWORD *)(v253 + 48) = *(_QWORD *)(v28 + 4408);
            if ( *(_QWORD *)(*(_QWORD *)(v26 + 112) + 88LL) >= *(_QWORD *)(*(_QWORD *)(v26 + 112) + 80LL) )
            {
              LOBYTE(v28) = 1;
              sub_94BEC0(a1: v26, a2: v28); // <-- luaC_step
            }
            v30 = *(_BYTE *)(v26 + 1);
            if ( (v30 & 4) != 0 )
            {
              v31 = *(_QWORD *)(v26 + 112);
              *(_BYTE *)(v26 + 1) = v30 & 0xFB;
```

So the offset is 0x94BEC0
