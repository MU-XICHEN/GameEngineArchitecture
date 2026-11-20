# Development Workflow

## Project language

Use English for project content, including source identifiers and comments, build and configuration files, documentation, UI text, and diagnostics. Use the English roadmap for development and keep the Chinese roadmap synchronized as a companion translation. Reply in the language the user uses, or follow an explicit language request.

## Starting a session

1. Read the [English roadmap](roadmap.en.md) and find the last row in **Progress handoff**. Use its ID, such as M01.01, to find the group's prerequisites, reading references, and completion check. Give each submodule its own checklist line.
2. When the user asks to continue, pick up from that handoff. Follow the current request when the user names a specific section, module, or question. If the handoff differs from the project state, check the implementation and actual run results.
3. When explaining the book, consult the local volume and cite the volume and section. Identify whether a page number is from the PDF or the printed book. Attribute ideas to the book or to Alder's own implementation choices. Start with an intuitive example, then introduce the terms, equations, or code needed to explain it.

## Working through a module

- **Reading.** Explain the problem the module solves, its dependencies, and how higher-level code will use it. If the user requests an explanation or review, keep the work within that scope. Use the user's feedback to track reading progress.
- **Implementation.** Check the existing code and follow the established toolchain and conventions. Explain the minimal interface, data ownership, and lifecycle, then integrate the module into the sample. The engine library provides reusable functionality. The sample implements the game rules.
- **Verification.** Follow the roadmap's completion check. Record the actual build or run commands, observed results, and open issues. Once the check passes, mark the item `- [x]` and record the result in the handoff.
- **Handoff.** Update the status at the end of the roadmap. If the active module changes, also update **Current progress** at the top. Record toolchain, coordinate system, or graphics backend decisions and their reasons beside the relevant module.
- **Roadmap maintenance.** Update module IDs, reading references, completion checks, checkboxes, and handoff entries in both language versions in the same change. See the [Chinese translation](roadmap.zh-CN.md).
