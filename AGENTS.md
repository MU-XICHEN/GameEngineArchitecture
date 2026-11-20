# GameEngineArchitecture Project Guide

This project uses both volumes of Jason Gregory's fourth edition of *Game Engine Architecture*. The user reads the relevant sections before implementing each C++ engine module with the assistant. The books are in `reading_lists/`.

The engine is designed for multiple platforms, with Windows as the first implementation and verification target. Use portable interfaces in the core and gameplay code. Keep Windows APIs and SDK types inside the corresponding platform implementation or device backend. Define interfaces as modules need them. Add the second platform after the target is chosen, and record which platforms were actually verified.

The planned build targets are the Engine library, the standalone Editor, and the standalone Sandbox sample. Both applications share the world, resources, rendering, and scene I/O. Editor owns the panels, selection state, and editor camera. The roadmap links to Hazel commits that show how comparable features evolved. Use those examples where they fit Alder's 3D and cross-platform goals.

## Project language

Use English for project content, including source identifiers and comments, build and configuration files, documentation, UI text, and diagnostics. Use the English roadmap for development and keep the Chinese roadmap synchronized as a companion translation. Reply in the language the user uses, or follow an explicit language request.

## Starting a session

1. Read the [English roadmap](docs/roadmap.en.md) and find the last row in **Progress handoff**. Use its ID, such as M01.01, to find the group's prerequisites, reading references, and completion check. Give each submodule its own checklist line.
2. When the user asks to continue, pick up from that handoff. Follow the current request when the user names a specific section, module, or question. If the handoff differs from the project state, check the implementation and actual run results.
3. When explaining the book, consult the local volume and cite the volume and section. Identify whether a page number is from the PDF or the printed book. Attribute ideas to the book or to Alder's own implementation choices. Start with an intuitive example, then introduce the terms, equations, or code needed to explain it.

## CMake build conventions

`Alder/` is the engine project root. Keep source files, dependencies, and builds there. The outer repository holds the development roadmaps, project guidance, and reference material.

[Alder/CMakeLists.txt](Alder/CMakeLists.txt) defines the C++20 executable target `Alder` from [Alder/main.cpp](Alder/main.cpp). Declare source files, compiler requirements, and dependencies per CMake target. Define Engine, Editor, and Sandbox inside `Alder/` when they are implemented. Editor and Sandbox link to Engine.

Open `Alder/` directly in Visual Studio or VS Code. From that directory, use these commands to configure, build, and run the Windows x64 Debug and Release variants.

```powershell
cmake -S . -B build -G "Visual Studio 18 2026" -A x64
cmake --build build --config Debug
./build/Debug/Alder.exe
cmake --build build --config Release
./build/Release/Alder.exe
```

Place generated project files and build outputs in `Alder/build/`, which Git ignores. On other platforms, select the appropriate generator and compiler in a separate build directory and reuse `Alder/CMakeLists.txt`. See the [Alder README](Alder/README.md) for prerequisites.

## Working through a module

- **Reading.** Explain the problem the module solves, its dependencies, and how higher-level code will use it. If the user requests an explanation or review, keep the work within that scope. Use the user's feedback to track reading progress.
- **Implementation.** Check the existing code and follow the established toolchain and conventions. Explain the minimal interface, data ownership, and lifecycle, then integrate the module into the sample. The engine library provides reusable functionality. The sample implements the game rules.
- **Verification.** Follow the roadmap's completion check. Record the actual build or run commands, observed results, and open issues. Once the check passes, mark the item `- [x]` and record the result in the handoff.
- **Handoff.** Update the status at the end of the roadmap. If the active module changes, also update **Current progress** at the top. Record toolchain, coordinate system, or graphics backend decisions and their reasons beside the relevant module.
- **Roadmap maintenance.** Update module IDs, reading references, completion checks, checkboxes, and handoff entries in both language versions in the same change. See the [Chinese translation](docs/roadmap.zh-CN.md).

## Commit messages

Write commit subjects in English using `<type>: <summary>`. Choose the prefix that describes the main change.

| Type | Use |
| --- | --- |
| `feat` | Add functionality |
| `fix` | Fix a problem |
| `refactor` | Restructure code while preserving observable behavior |
| `docs` | Update documentation |
| `test` | Add or update tests |
| `chore` | Perform routine maintenance or configure tools |
| `build` | Change the build system or build dependencies |
| `ci` | Update continuous integration |
