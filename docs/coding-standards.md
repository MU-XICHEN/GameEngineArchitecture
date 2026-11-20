# Alder Coding Standards

Apply these conventions when writing or modifying Alder code. Use English for names and comments.

## Code comments

- Prefer one short, plain-English sentence per comment.
- Document public interfaces at their declarations. Include the details callers need to use them correctly.
- Explain non-obvious implementation choices, edge cases, or platform assumptions next to the relevant code.
- In `CMakeLists.txt`, explain target roles and build decisions that need context.
- Update comments when the behavior they describe changes.

## C++ formatting

Format each changed C++ source or header file after editing and before verification. The [Alder clang-format configuration](../Alder/.clang-format) captures the Visual Studio style used by the Microsoft C/C++ extension for VS Code (`ms-vscode.cpptools`).

In VS Code, use **Format Document** with the C/C++ extension. From a terminal, use the extension's bundled `clang-format` when available and run `clang-format --style=file -i <file>` for each changed file. Both use the same project configuration.

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
