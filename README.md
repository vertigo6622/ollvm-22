<p>
  <d><strong>ollvm-22</strong></d>
  <br/>
  <sup>obfuscator llvm 22</sup>
  <br/>
  <a href="https://deepwiki.com/vertigo6622/ollvm-22"><img src="https://deepwiki.com/badge.svg" alt="Ask DeepWiki"></a>
</p>

<p>ollvm (obfuscator llvm) plugin ported to llvm 22.1.1. add bogus control flow, flattening, splitting, substitution to obfuscate your C/C++ code.</p>

# usage:

**use with clang:**
```
clang -fpass-plugin=libObfuscation.so -mllvm -fla -mllvm -bcf -mllvm -sub -mllvm -split file.c -o output-file
```

**compile:**

*llvm installed via brew:*

```
cd ollvm-22 && mkdir build && cd build && cmake ../obfuscation && make
```

*llvm anywhere else:*
```
cd ollvm-22 && mkdir build && cd build && cmake -DLLVM_DIR=<llvm location> ../obfuscation && make
```

---

<sup>this repo was created as part of the  `obsidian protector - x64 pe packer` project found [here](https://github.com/vertigo6622/obsidian-protector)</sup>
