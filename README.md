# ollvm-22
ollvm-16 (obfuscator llvm) plugin ported to llvm 22.1.1. add bogus control flow, flattening, splitting, substitution to obfuscate your C/C++ code.

# usage:
**compile:**
*llvm installed via brew:*
`cd ollvm-22 && mkdir build && cd build && cmake ../obfuscation && make`
*llvm anywhere else:*
`cd ollvm-22 && mkdir build && cd build && cmake -DLLVM_DIR=<llvm location> ../obfuscation && make`

**use with clang:**
`clang -fpass-plugin=libObfuscation.so -mllvm -fla -mllvm -bcf -mllvm -sub -mllvm -split file.c -o output-file`

