# Dev Log

Add a dated entry for each implementation change, including revisions made during acceptance. Include the roadmap module ID when applicable. Describe the behavior, the relevant design decisions, and the files that implement them.

## 2026-11-20 · Initial CMake application

- [CMakeLists.txt](../Alder/CMakeLists.txt) defines the `Alder` executable from `main.cpp`, requires C++20 for that target, and disables compiler extensions.
- [main.cpp](../Alder/main.cpp) defines the console entry point. It writes `Hello, Alder!` to standard output and exits successfully.
