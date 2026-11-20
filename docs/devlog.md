# Dev Log

Add a dated entry for each implementation change, including revisions made during acceptance. Include the roadmap module ID when applicable. Describe the behavior, the relevant design decisions, and the files that implement them.

## 2026-11-20 · Initial CMake application

- [CMakeLists.txt](../Alder/CMakeLists.txt) defines the `Alder` executable from `main.cpp`, requires C++20 for that target, and disables compiler extensions.
- [main.cpp](../Alder/main.cpp) defines the console entry point. It writes `Hello, Alder!` to standard output and exits successfully.

## 2026-11-20 — M01.02 Engine library target

- [CMakeLists.txt](../Alder/CMakeLists.txt) defines the `Engine` static library target, compiles it as C++20 with compiler extensions disabled, and exposes `Engine/include` to consumers that link the target.
- [Version.h](../Alder/Engine/include/Alder/Version.h) declares `Alder::GetVersion() noexcept`. [Version.cpp](../Alder/Engine/src/Version.cpp) defines the function in the library. It returns the integer `1` and requires no runtime state.

## 2026-11-20 · Shared C++ formatting

- [Alder/.clang-format](../Alder/.clang-format) defines the shared style for VS Code and command-line formatting. It follows the C/C++ extension's Visual Studio fallback with four-space indentation, Allman braces, and no automatic line-length limit.

## 2026-11-20 · M01.02 Version query documentation

- [Version.h](../Alder/Engine/include/Alder/Version.h) documents that the integer version query is available without engine initialization.

## 2026-11-20 · M01.02 Engine version check linkage

- [CMakeLists.txt](../Alder/CMakeLists.txt) links the `Alder` executable to `Engine`. This gives `main.cpp` the public header search path and links the implementation of `Alder::GetVersion()` from the static library.
