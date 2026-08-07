# GetLuaStateForInstance

Search "Script Start", and look bit up:
```c
            }
            v25 = (_DWORD *)sub_2316530(a1: v24 + 312, a2: v247, a3: &v274);
            LODWORD(v295) = *v25 - (_DWORD)v25;
            HIDWORD(v295) = v25[1] - (_DWORD)v25;
            v26 = v295;
            if ( *((_QWORD *)&v274 + 1) != 0 )
              sub_799660(a1: *((volatile signed __int32 **)&v274 + 1)); // <-- GetLuaStateForInstance
            if ( v26 != 0 )
            {
              v27 = *(_QWORD *)(v26 + 32);
              v28 = *(_QWORD *)(*(_QWORD *)(v27 + 24) + 16LL);
            }
            else
            {
              v27 = 0;
              v28 = *(_QWORD *)(*(_QWORD *)&word_18 + 16LL);
            }
          }
          __unwind
          {
            sub_79AA00(a1: &v274);
          }
          __eh34_enter_wind_state(6, 7);
          v29 = *(_QWORD *)(*(_QWORD *)(v27 + 24) + 40LL);
          v253 = v29;
          v254 = *(_QWORD *)(v29 + 312);
          *(_QWORD *)(v29 + 312) = "Script Start"; // <-- YOU'LL BE PUT HERE
          if ( *(int *)(v28 + 4784) >= 3 )
          {
            v243 = "sor.png";
            sub_2C9AD80(a1: 0, a2: (__int64)&aTexturesCursor_5[-1021808]);
          }
          if ( __eh34_unwind(7) )
            goto unwind_state_7;
          __eh34_exit_wind_state(7, 6);
```

So the offset is 0x799660
