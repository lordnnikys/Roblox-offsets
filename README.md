# Roblox-offsets
This is guide on how to get multiple roblox offsets through ida

Time spent: 12 hours

986 lines

35731 characters

**SOME OFFSETS CAN BE PRESENT MULTIPLE TIMES, BECAUSE I'M INATTENTIVE AND I DONT KEEP TRACK OF WHAT I ALREADY DID!!!!**

List of current offsets:

Lua_NewThread

Require Bypass

Lua_SandBoxThread

lua_createtable

lua_setmetatable

lua_pushstring (2 guides on it here)

lua_pushvalue

lua_settable

lua_replace

Lua_pseudoaddr

LuaO_nilobject

luaC_barrierf

luaG_runerror

lua_rawcheckstack

luaD_throw

luaG_addinfo

luaL_argerrorL

luaL_errorL

GetLuaStateForInstance

AttachRobloxExtraSpace

lua_setfield

pushinstance

TaskDefer

GetIdentityStruct

luaS_newlstr (2 guides in here)

luau_load

luaC_step (~4 guides on it here)

lua_loadsafe

luaD_rawrunprotected

luaM_free_

luaC_barrierback

lua_resume

lua_pushnumber

lua_pushinteger

lua_gettop

lua_settop

luaL_errorL

luaA_toobject

lua_encodepointer

luaL_tostring

luaL_checklstring

lua_gc

lua_tonumber

lua_getmetatable

lua_type

lua_setfield

luaL_register

lua_getfield

luaB_assert

luaB_error	

luaB_gcinfo	

luaB_getfenv	

luaB_getmetatable	

luaB_next	

luaB_newproxy	

luaB_print	

luaB_rawequal	

luaB_rawget	

luaB_rawlen	

luaB_rawset	

luaB_select	

luaB_setfenv

luaB_setmetatable

luaB_tonumber

luaB_tostring

lua_pcall

coroutine.create

coroutine.resume

coroutine.yield

coroutine.wrap

coroutine.close

coroutine.isyieldable

coroutine.running

coroutine.status

lua_setfield (C API)

FireServer

FireClient

lua_pushcclosure

lua_pushcfunction

ScriptContextResume

NewInstance

Impersonator

GetCapabilities

TouchInterest

TaskCancel

SetFFlag

InvokeServer
