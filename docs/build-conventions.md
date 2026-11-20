# CMake Build Conventions

`Alder/` is the engine project root. Keep source files, dependencies, and builds there. The outer repository holds the development roadmaps, project guidance, and reference material.

[Alder/CMakeLists.txt](../Alder/CMakeLists.txt) defines the C++20 executable target `Alder` from [Alder/main.cpp](../Alder/main.cpp). Declare source files, compiler requirements, and dependencies per CMake target. Define Engine, Editor, and Sandbox inside `Alder/` when they are implemented. Editor and Sandbox link to Engine.

Open `Alder/` directly in Visual Studio or VS Code. The [Alder README](../Alder/README.md#build-on-windows) has the prerequisites and commands to configure, build, and run the Windows x64 Debug and Release variants.

Place generated project files and build outputs in `Alder/build/`, which Git ignores. On other platforms, select the appropriate generator and compiler in a separate build directory and reuse `Alder/CMakeLists.txt`.
