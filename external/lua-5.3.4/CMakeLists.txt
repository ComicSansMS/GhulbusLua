cmake_minimum_required(VERSION 3.0)

project(lua C)

set(LUA_SOURCE_DIR ${PROJECT_SOURCE_DIR}/src)

set(LUA_HEADER_FILES
    ${LUA_SOURCE_DIR}/lapi.h
    ${LUA_SOURCE_DIR}/lauxlib.h
    ${LUA_SOURCE_DIR}/lcode.h
    ${LUA_SOURCE_DIR}/lctype.h
    ${LUA_SOURCE_DIR}/ldebug.h
    ${LUA_SOURCE_DIR}/ldo.h
    ${LUA_SOURCE_DIR}/lfunc.h
    ${LUA_SOURCE_DIR}/lgc.h
    ${LUA_SOURCE_DIR}/llex.h
    ${LUA_SOURCE_DIR}/llimits.h
    ${LUA_SOURCE_DIR}/lmem.h
    ${LUA_SOURCE_DIR}/lobject.h
    ${LUA_SOURCE_DIR}/lopcodes.h
    ${LUA_SOURCE_DIR}/lparser.h
    ${LUA_SOURCE_DIR}/lprefix.h
    ${LUA_SOURCE_DIR}/lstate.h
    ${LUA_SOURCE_DIR}/lstring.h
    ${LUA_SOURCE_DIR}/ltable.h
    ${LUA_SOURCE_DIR}/ltm.h
    ${LUA_SOURCE_DIR}/lua.h
    ${LUA_SOURCE_DIR}/lua.hpp
    ${LUA_SOURCE_DIR}/luaconf.h
    ${LUA_SOURCE_DIR}/lualib.h
    ${LUA_SOURCE_DIR}/lundump.h
    ${LUA_SOURCE_DIR}/lvm.h
    ${LUA_SOURCE_DIR}/lzio.h
)

set(LUA_CORE_SOURCE_FILES
    ${LUA_SOURCE_DIR}/lapi.c
    ${LUA_SOURCE_DIR}/lcode.c
    ${LUA_SOURCE_DIR}/lctype.c
    ${LUA_SOURCE_DIR}/ldebug.c
    ${LUA_SOURCE_DIR}/ldo.c
    ${LUA_SOURCE_DIR}/ldump.c
    ${LUA_SOURCE_DIR}/lfunc.c
    ${LUA_SOURCE_DIR}/lgc.c
    ${LUA_SOURCE_DIR}/llex.c
    ${LUA_SOURCE_DIR}/lmem.c
    ${LUA_SOURCE_DIR}/lobject.c
    ${LUA_SOURCE_DIR}/lopcodes.c
    ${LUA_SOURCE_DIR}/lparser.c
    ${LUA_SOURCE_DIR}/lstate.c
    ${LUA_SOURCE_DIR}/lstring.c
    ${LUA_SOURCE_DIR}/ltable.c
    ${LUA_SOURCE_DIR}/ltm.c
    ${LUA_SOURCE_DIR}/lundump.c
    ${LUA_SOURCE_DIR}/lvm.c
    ${LUA_SOURCE_DIR}/lzio.c
)

set(LUA_LIBRARY_SOURCE_FILES
    ${LUA_SOURCE_DIR}/lauxlib.c
    ${LUA_SOURCE_DIR}/lbaselib.c
    ${LUA_SOURCE_DIR}/lbitlib.c
    ${LUA_SOURCE_DIR}/lcorolib.c
    ${LUA_SOURCE_DIR}/ldblib.c
    ${LUA_SOURCE_DIR}/liolib.c
    ${LUA_SOURCE_DIR}/lmathlib.c
    ${LUA_SOURCE_DIR}/loslib.c
    ${LUA_SOURCE_DIR}/lstrlib.c
    ${LUA_SOURCE_DIR}/ltablib.c
    ${LUA_SOURCE_DIR}/lutf8lib.c
    ${LUA_SOURCE_DIR}/loadlib.c
    ${LUA_SOURCE_DIR}/linit.c
)

add_library(liblua STATIC ${LUA_HEADER_FILES} ${LUA_CORE_SOURCE_FILES} ${LUA_LIBRARY_SOURCE_FILES})
target_include_directories(liblua PUBLIC ${LUA_SOURCE_DIR})

add_executable(lua ${LUA_SOURCE_DIR}/lua.c)
target_link_libraries(lua PRIVATE liblua)
add_executable(luac ${LUA_SOURCE_DIR}/luac.c)
target_link_libraries(luac PRIVATE liblua)
