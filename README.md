# Cross platform toolchain setup for Apple Silicon host

## Install toolchains 
- for MacOS simply `Clang`

- for Linux available via homebrew, here:
https://github.com/messense/homebrew-macos-cross-toolchains

- for Windows
`brew install mingw-w64`

## The bash/zsh profile
```zsh
alias linux_x64_cxx="x86_64-unknown-linux-gnu-g++"
alias linux_x86_cxx="i686-unknown-linux-gnu-g++"
alias linux_x64_cc="x86_64-unknown-linux-gnu-gcc"
alias linux_x86_cc="i686-unknown-linux-gnu-gcc"

alias apple_x64_cxx="clang -mmacosx-version-min=10.15 -arch x86_64"
alias apple_arm64_cxx="clang -mmacosx-version-min=10.15 -arch x86_64"
alias apple_x64_cc"clang -mmacosx-version-min=10.15 -arch x86_64"
alias apple_arm64_cc="clang -mmacosx-version-min=10.15 -arch x86_64"

alias windows_x86_cxx="i686-w64-mingw32-g++"
alias windows_x86_cc="i686-w64-mingw32-gcc"
alias windows_x64_cxx="x86_64-w64-mingw32-g++"
alias windows_x64_cc="x86_64-w64-mingw32-gcc"
```

# Example compilation commands
## OSX
### x86_64
- executable: `apple_x64_cxx -o osx/x86_64 main.cpp`

- shared: `apple_x64_cc -o osx/x86_64.so -shared lib.c`

- dynamiclib: `apple_x64_cc -o osx/x86_64.dylib -dynamiclib lib.c`
### arm64
- executable: `apple_arm64_cxx -o osx/arm64 main.cpp`

- shared: `apple_arm64_cc -o osx/arm64.so -shared lib.c`

- dynamiclib: `apple_arm64_cc -o osx/arm64.dylib -dynamiclib lib.c`

## Linux
### x86_64
- executable: `linux_x64_cxx -o linux/x86_64 main.cpp`

- shared: `linux_x64_cc -o linux/x86_64.so -shared lib.c`
### x86
- executable: `linux_x86_cxx -o linux/x86 main.cpp`

- shared: `linux_x86_cc -o linux/x86.so -shared lib.c`

## Windows
### x86_64
- executable: `windows_x64_cxx -o windows/x86_64.exe main.cpp`

- shared: `windows_x64_cc -o windows/x86_64.dll -shared lib.c`
### x86
- executable: `windows_x86_cxx -o windows/x86.exe main.cpp`

- shared: `windows_x86_cc -o windows/x86.dll -shared lib.c`

