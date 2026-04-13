MacOS p2996 (CPP26 reflection) bloomberg toolchain:

Clone this repo to:
```
git clone git@github.com:justinmichaud/p2996.xctoolchain.git /Users/$USER/Library/Developer/Toolchains/p2996.xctoolchain/
cd /Users/$USER/Library/Developer/Toolchains/p2996.xctoolchain/
ln -s /Users/$USER/clang-p2996 usr
```

Clone bloomberg:
```
git clone  https://github.com/bloomberg/clang-p2996.git /Users/$USER/clang-p2996
cd /Users/$USER/clang-p2996
git checkout p2996
cmake -G Ninja -S llvm -B build -DCMAKE_BUILD_TYPE=Release -DLLVM_ENABLE_PROJECTS="clang" -DLLVM_ENABLE_RUNTIMES="libcxx;libcxxabi;libunwind" -DCMAKE_INSTALL_PREFIX=/Users/$USER/clang-p2996/install
ninja -C build
```

Build WebKit:
```
Tools/Scripts/build-webkit --release --export-compile-commands COMPILATION_CACHE_ENABLE_CACHING=NO CLANG_ENABLE_EXPLICIT_MODULES=NO _EXPERIMENTAL_SWIFT_EXPLICIT_MODULES=NO ENABLE_WK_LIBRARY_MODULE_VERIFIER=NO OVERRIDE_ENABLE_MODULE_VERIFIER=NO ENABLE_MODULE_VERIFIER=NO CPLUSPLUS=/Users/$USER/Library/Developer/Toolchains/p2996.xctoolchain/usr-wrapper/bin/clang++
```