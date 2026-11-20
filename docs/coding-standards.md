# Alder Coding Standards

Apply these conventions when writing or modifying Alder code. Use English for names and comments.

## C++ file names

- Name an executable's entry-point file `main.cpp`.
- Use PascalCase for other C++ source and header file names. Match the name of the main class or module in the file.
- Give a header and its implementation the same base name. Use `.h` for the header and `.cpp` for the implementation.
- Use the exact spelling and capitalization of the file on disk in each `#include` and CMake source path so it resolves on case-sensitive filesystems.

| Purpose | File names |
| --- | --- |
| Executable entry point | `main.cpp` |
| Logger | `Logger.h`, `Logger.cpp` |
| Resource manager | `ResourceManager.h`, `ResourceManager.cpp` |
| Windows window implementation | `Win32Window.h`, `Win32Window.cpp` |
| Logger tests | `LoggerTests.cpp` |
