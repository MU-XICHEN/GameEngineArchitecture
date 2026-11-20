# Alder Project Overview

This project uses both volumes of Jason Gregory's fourth edition of *Game Engine Architecture*. The user reads the relevant sections before implementing each C++ engine module with the assistant. The books are in `reading_lists/`.

The engine is designed for multiple platforms, with Windows as the first implementation and verification target. Use portable interfaces in the core and gameplay code. Keep Windows APIs and SDK types inside the corresponding platform implementation or device backend. Define interfaces as modules need them. Add the second platform after the target is chosen, and record which platforms were actually verified.

The planned build targets are the Engine library, the standalone Editor, and the standalone Sandbox sample. Both applications share the world, resources, rendering, and scene I/O. Editor owns the panels, selection state, and editor camera. The roadmap links to Hazel commits that show how comparable features evolved. Use those examples where they fit Alder's 3D and cross-platform goals.
