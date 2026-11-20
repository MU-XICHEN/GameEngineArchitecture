# GameEngineArchitecture Project Guide

Use English for project content, including source identifiers and comments, build and configuration files, documentation, progress handoffs, UI text, diagnostics, and commit messages.

Use the language of the user's message for progress updates and replies.

- Before creating or modifying source code, read and follow the [coding standards](docs/coding-standards.md).
- Record the technical details of each implementation change in the [development log](docs/devlog.md).
- Before committing, follow the [commit message conventions](docs/commit-messages.md).

## Project overview

This project uses both volumes of Jason Gregory's fourth edition of *Game Engine Architecture*. The user reads the relevant sections before implementing each C++ engine module with the assistant. The books are in `reading_lists/`.

The engine is designed for multiple platforms, with Windows as the first implementation and verification target. Use portable interfaces in the core and gameplay code. Keep Windows APIs and SDK types inside the corresponding platform implementation or device backend. Define interfaces as modules need them. Add the second platform after the target is chosen, and record which platforms were actually verified.

The planned build targets are the Engine library, the standalone Editor, and the standalone Sandbox sample. Both applications share the world, resources, rendering, scene I/O, and the code that implements the room's game rules. Editor owns the panels, selection state, and editor camera.

### Platform independence

Use standard C++ or engine types in math, resources, world objects, and gameplay. Prefer standard C++ facilities for clocks, files, and threads where they meet the requirements. Have the build target select the platform implementation when native facilities are needed.

Translate device input into engine keys or actions. Choose the graphics API in M08.01 and keep native graphics and audio device types inside their respective backends. Store resource IDs or relative paths in scene files.

For a second platform, reuse the core, gameplay, and sample assets and add the required platform implementations. Verify window creation, input, and triangle rendering first. Then run the room and check sound, pickups, and restart. Record the checks that pass on each platform.

## Development workflow

### Starting a session

1. Read the last row in the [progress handoff](docs/progress-handoff.md). Use its ID, such as M01.01, to find the group's prerequisites, reading references, and completion check in the [roadmap](docs/roadmap.en.md). Give each submodule its own checklist line.
2. When the user asks to continue, pick up from that handoff. Follow the current request when the user names a specific section, module, or question. If the handoff differs from the project state, check the implementation and actual run results.
3. When explaining the book, consult the local volume and cite the volume and section. Identify whether a page number is from the PDF or the printed book. Attribute ideas to the book or to Alder's own implementation choices. Start with an intuitive example, then introduce the terms, equations, or code needed to explain it.

### Working through a module

- **Reading.** For reading-only items, give the volume, section, and any relevant pages or figures. Use the user's feedback to track reading progress. If the user requests an explanation or review, keep the work within that scope.
- **Implementation.** Check the existing code and follow the established toolchain and conventions. Explain the minimal interface, data ownership, and lifecycle, then integrate the module into the sample. The engine library provides reusable functionality. The sample implements the game rules.
- **Verification.** For implementation items, follow the roadmap's completion check and record the result in the [progress handoff](docs/progress-handoff.md). When implementation and verification are complete, set the status to **Awaiting user acceptance**. Summarize what changed and what the user can check.
- **User acceptance.** Keep the current item active and its roadmap checkbox open while awaiting the user's approval. If the user requests changes, address them in the same item and return it for review. After the user confirms acceptance, set the status to **Accepted**, mark the roadmap item `- [x]`, and advance the handoff to the next item.
- **Handoff.** Update the [progress handoff](docs/progress-handoff.md). Its last row identifies the current module. Record toolchain, coordinate system, or graphics backend decisions and their reasons beside the relevant module.

## CMake build conventions

`Alder/` is the engine project root. Keep source files, dependencies, and builds there. The outer repository holds the development roadmaps, project guidance, and reference material.

[Alder/CMakeLists.txt](Alder/CMakeLists.txt) defines the C++20 executable target `Alder` from [Alder/main.cpp](Alder/main.cpp). Declare source files, compiler requirements, and dependencies per CMake target. Define Engine, Editor, and Sandbox inside `Alder/` when they are implemented. Editor and Sandbox link to Engine.

Open `Alder/` directly in Visual Studio or VS Code. The [Alder README](Alder/README.md#build-on-windows) has the prerequisites and commands to configure, build, and run the Windows x64 Debug and Release variants.

Place generated project files and build outputs in `Alder/build/`, which Git ignores. On other platforms, select the appropriate generator and compiler in a separate build directory and reuse `Alder/CMakeLists.txt`.
