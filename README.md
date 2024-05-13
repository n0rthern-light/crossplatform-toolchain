# Cross platform toolchain setup for Apple Silicon host

## Install toolchains 
- for MacOS simply `Clang`

- for Linux available via homebrew, here:
https://github.com/messense/homebrew-macos-cross-toolchains

- for Windows
`brew install mingw-w64`

## Setup PATH
```zsh
export PATH="/opt/homebrew/Cellar/i686-unknown-linux-gnu/13.2.0/toolchain/bin:$PATH"
export PATH="/opt/homebrew/Cellar/x86_64-unknown-linux-gnu/13.2.0/toolchain/bin:$PATH"
export PATH="/opt/homebrew/Cellar/mingw-w64/11.0.1_1/toolchain-i686/bin:$PATH"
export PATH="/opt/homebrew/Cellar/mingw-w64/11.0.1_1/toolchain-x86_64/bin:$PATH"
```

## The bash/zsh profile
```zsh
alias linux_x64_cxx="x86_64-unknown-linux-gnu-g++"
alias linux_x86_cxx="i686-unknown-linux-gnu-g++"
alias linux_x64_c="x86_64-unknown-linux-gnu-gcc"
alias linux_x86_c="i686-unknown-linux-gnu-gcc"

alias apple_x64_cxx="clang -mmacosx-version-min=10.15 -arch x86_64"
alias apple_arm64_cxx="clang -mmacosx-version-min=10.15 -arch x86_64"
alias apple_x64_c"clang -mmacosx-version-min=10.15 -arch x86_64"
alias apple_arm64_c="clang -mmacosx-version-min=10.15 -arch x86_64"

alias windows_x86_cxx="i686-w64-mingw32-g++"
alias windows_x86_c="i686-w64-mingw32-gcc"
alias windows_x64_cxx="x86_64-w64-mingw32-g++"
alias windows_x64_c="x86_64-w64-mingw32-gcc"
```

# Example compilation commands
## OSX
### x86_64
- executable: `apple_x64_cxx -o osx/x86_64 main.cpp`

- shared: `apple_x64_c -o osx/x86_64.so -shared lib.c`

- dynamiclib: `apple_x64_c -o osx/x86_64.dylib -dynamiclib lib.c`
### arm64
- executable: `apple_arm64_cxx -o osx/arm64 main.cpp`

- shared: `apple_arm64_c -o osx/arm64.so -shared lib.c`

- dynamiclib: `apple_arm64_c -o osx/arm64.dylib -dynamiclib lib.c`

## Linux
### x86_64
- executable: `linux_x64_cxx -o linux/x86_64 main.cpp`

- shared: `linux_x64_c -o linux/x86_64.so -shared lib.c`
### x86
- executable: `linux_x86_cxx -o linux/x86 main.cpp`

- shared: `linux_x86_c -o linux/x86.so -shared lib.c`

## Windows
### x86_64
- executable: `windows_x64_cxx -o windows/x86_64.exe main.cpp`

- shared: `windows_x64_c -o windows/x86_64.dll -shared lib.c`
### x86
- executable: `windows_x86_cxx -o windows/x86.exe main.cpp`

- shared: `windows_x86_c -o windows/x86.dll -shared lib.c`

