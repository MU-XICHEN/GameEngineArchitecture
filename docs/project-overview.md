# Alder Project Overview

This project uses both volumes of Jason Gregory's fourth edition of *Game Engine Architecture*. The user reads the relevant sections before implementing each C++ engine module with the assistant. The books are in `reading_lists/`.

The engine is designed for multiple platforms, with Windows as the first implementation and verification target. Use portable interfaces in the core and gameplay code. Keep Windows APIs and SDK types inside the corresponding platform implementation or device backend. Define interfaces as modules need them. Add the second platform after the target is chosen, and record which platforms were actually verified.

The planned build targets are the Engine library, the standalone Editor, and the standalone Sandbox sample. Both applications share the world, resources, rendering, scene I/O, and the code that implements the room's game rules. Editor owns the panels, selection state, and editor camera.

## Platform independence

Use standard C++ or engine types in math, resources, world objects, and gameplay. Prefer standard C++ facilities for clocks, files, and threads where they meet the requirements. Have the build target select the platform implementation when native facilities are needed.

Translate device input into engine keys or actions. Choose the graphics API in M08.01 and keep native graphics and audio device types inside their respective backends. Store resource IDs or relative paths in scene files.

For a second platform, reuse the core, gameplay, and sample assets and add the required platform implementations. Verify window creation, input, and triangle rendering first. Then run the room and check sound, pickups, and restart. Record the checks that pass on each platform.
