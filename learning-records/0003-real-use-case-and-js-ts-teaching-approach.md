# Real use case is general software (CLI/TUI/web), not robotics; teach TS+JS together

The user's actual driver for learning TS is reading/maintaining AI-generated TypeScript in general software contexts — they ran into this directly while building a TUI component for a coding agent and couldn't read the generated TS at all. Robotics/Python was only ever meant as a comfort-language analogy, not the example domain. Long-term the user wants TS as the core of a software/web stack, then to add a framework (Node/React) once fundamentals are solid. `MISSION.md` updated accordingly: examples should now be CLI tools, scripts, small TUI/agent code, and simple API/web snippets.

## JS vs TS learning order

The user asked whether to learn JS first (as "the mother language") or focus on TS. Quick research into current developer surveys/community advice (State of JS 2024 — TypeScript adoption ~78%, with 67% of developers writing more TS than JS; common advice on dev forums is "learn JS basics, then TS for real projects") shows TS is now the de facto default for production code, and AI-generated code the user encounters is overwhelmingly TS. Decision: teach **TS-primary**, but explicitly call out which features in any snippet are plain JavaScript (run at runtime — arrow functions, `import`/`export`, array methods like `map`/`filter`/`reduce`, `async`/`await`) vs TypeScript-only (compile-time-only — `: type` annotations, `interface`, generics' type parameters). This avoids a separate JS curriculum while still giving the user a mental model of "what survives compilation."

## Implications for future lessons
- Lesson 3 onward: examples drawn from CLI/TUI/script/API contexts, not robotics.
- Introduce a lightweight "JS" / "TS" tag convention in lessons to mark which syntax is which, building toward "I can read any real .ts file."
- Priority order for upcoming lessons: arrow functions + modules (import/export) → array methods → async/await + Promise\<T\> → generics → classes/TUI component shapes.
