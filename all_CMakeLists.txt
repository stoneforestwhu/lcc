# cmake minimum version required
cmake_minimum_required (VERSION 2.8)
# project information

project(LCC)

if(MSVC) 
    add_definitions(-D_CRT_SECURE_NO_WARNINGS) 
endif()

include_directories(x86/win32)
include_directories(src)

set(BRCC_SOURCES
    src/alloc.c 
	src/bind.c 
	src/dag.c 
	src/decl.c
	src/enode.c
	src/error.c
	src/event.c
	src/expr.c
	src/gen.c
	src/init.c
	src/inits.c
	src/input.c
	src/lex.c
	src/list.c
    src/main.c
    src/null.c
    src/output.c
    src/prof.c
    src/profio.c
    src/simp.c
    src/stmt.c
    src/string.c
    src/sym.c
    src/symbolic
    src/bytecode
    src/trace.c
    src/tree.c
    src/types.c
    src/stab.c
    backend/dagcheck.c
    backend/alpha.c
    backend/mips.c
    backend/sparc.c
    backend/x86.c
    backend/x86linux.c)

add_executable(rcc ${BRCC_SOURCES})


set(BPRINT_SOURCES
    etc/bprint.c)
add_executable(bprint ${BPRINT_SOURCES})

set(BOPS_SOURCES
    etc/ops.c)
add_executable(ops ${BOPS_SOURCES})

set(BLCC_SOURCES
    etc/lcc.c
	etc/win32.c)
add_executable(lcc ${BLCC_SOURCES})

set(BLIBLCC_SOURCES
    lib/assert.c
	lib/yynull.c
	lib/bbexit.c)
add_library(liblcc ${BLIBLCC_SOURCES})

set(BCPP_SOURCES
    cpp/cpp.c
    cpp/lex.c
    cpp/nlist.c
    cpp/tokens.c 
    cpp/macro.c 
    cpp/eval.c
    cpp/include.c
    cpp/hideset.c
    cpp/getopt.c
    cpp/unix.c)
add_executable(cpp ${BCPP_SOURCES})