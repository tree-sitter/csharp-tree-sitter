########
#
#	Tree-Sitter Base and Common Language Parsers
#

CFLAGS=/nologo /FC /Od /Z7 /Gy /diagnostics:column /Itree-sitter/lib/include
LFLAGS=/def:$(@B).def /incremental:no /debug

BIN=..\bin\debug\net7.0

DLLS=\
	$(BIN)/tree-sitter.dll \
	$(BIN)/tree-sitter-cpp.dll \

all: dirs $(DLLS)

dirs:
	@if not exist tree-sitter\lib\src\alloc.c echo.
	@if not exist tree-sitter\lib\src\alloc.c echo *** Error: Missing tree-sitter sources.  Did you use --recursive with git clone?
	@if not exist tree-sitter\lib\src\alloc.c echo.
	@if not exist $(BIN)\nul mkdir $(BIN)

########
#
# 	Tree-Sitter Base Library
#
$(BIN)/tree-sitter.obj: \
		tree-sitter/lib/src/alloc.c \
		tree-sitter/lib/src/get_changed_ranges.c \
		tree-sitter/lib/src/language.c \
		tree-sitter/lib/src/lexer.c \
		tree-sitter/lib/src/lib.c \
		tree-sitter/lib/src/node.c \
		tree-sitter/lib/src/parser.c \
		tree-sitter/lib/src/query.c \
		tree-sitter/lib/src/stack.c \
		tree-sitter/lib/src/subtree.c \
		tree-sitter/lib/src/tree.c \
		tree-sitter/lib/src/tree_cursor.c
	cl $(CFLAGS) /Fo:$@ \
		/Itree-sitter/lib/src /Itree-sitter/lib/src/unicode \
		/c tree-sitter/lib/src/lib.c

$(BIN)/tree-sitter.dll: $(BIN)/tree-sitter.obj
	cl /LD $(CFLAGS) /Fe:$@ $** /link $(LFLAGS)


########
#
#   C++
#
$(BIN)/tree-sitter-cpp-parser.obj: tree-sitter-cpp/src/parser.c
	cl $(CFLAGS) /Fo:$@ /Itree-sitter-cpp/src/include /c $**

$(BIN)/tree-sitter-cpp-scanner.obj: tree-sitter-cpp/src/scanner.c
	cl $(CFLAGS) /Fo:$@ /Itree-sitter-cpp/src/include /c $**

$(BIN)/tree-sitter-cpp.dll: $(BIN)/tree-sitter-cpp-parser.obj $(BIN)/tree-sitter-cpp-scanner.obj
	cl /LD $(CFLAGS) /Fe:$@ $** /link $(LFLAGS)

########
#
#	Clean
#
clean:
	-del *.obj $(BIN)\*.obj 2>nul
	-del $(BIN)\tree-sitter*.dll $(BIN)\tree-sitter*.exp $(BIN)\tree-sitter*.lib $(BIN)\tree-sitter*.pdb 2>nul
	-del tree-sitter*.dll tree-sitter*.exp tree-sitter*.lib tree-sitter*.pdb 2>nul
	-del $(BIN)\xred.* $(BIN)\test.exe $(BIN)\test.exp $(BIN)\test.pdb $(BIN)\test.lib 2>nul
	-del *~ 2>nul
	@-echo.
	@-echo.

########
#
#	
#

xt:
	xred -tree xpdb.cs > xpdb.tree && emacs xpdb.tree
	xred -tree vm_devices_net_netvsp_src_lib.rs > lib.tree && emacs lib.tree
	xred -tree minkernel_fs_ntfs_create.c > create.tree && emacs create.tree
	xred -tree dpx.cpp > dpx.tree && emacs dpx.tree

# End of File.
