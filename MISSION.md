# Mission: TypeScript

## Why
The user wants TypeScript to become the **core of their software/web development stack**. The immediate, practical driver is being able to read, trust-but-verify, and maintain TypeScript that AI tools generate for general software — CLI tools, TUI components (e.g. building a TUI for a coding agent), and eventually web apps — none of which is robotics-related. Today the user is stuck trusting AI output blindly because they can't read it. Long-term, once TS fundamentals are solid, the user wants to add a framework/platform (e.g. Node, React) on top to complete a professional full-stack toolkit.

## Success looks like
- Can read an AI-generated TypeScript function/interface and explain what every type annotation means
- Can read a real multi-file TS project: imports/exports, arrow functions, array methods (`map`/`filter`/`reduce`), and tell which parts are plain JavaScript vs TypeScript-only
- Can read `async`/`await` and `Promise<T>` code (the dominant pattern for anything that talks to a file, API, or process)
- Recognizes generics (`Array<T>`, `Promise<T>`, `Map<K, V>`, etc.) well enough to know "what's the placeholder for"
- Can confidently write basic typed functions, interfaces, and small scripts from scratch
- Can spot when AI-generated TypeScript is wrong or overly complex, and simplify it

## Constraints
- Mechanical engineer by background, not a programmer. Knows Python (and a bit of Arduino) — this is the home language used for analogies, not the example domain.
- **Examples should come from general software/web contexts** (CLI tools, scripts, small TUI/agent-style code, simple API/web snippets) — not robotics. Robotics was useful only as a starting analogy.
- Teach TS and JS **together, TS-primary**: TypeScript is JavaScript + types, and ~most real-world code today is TS (industry surveys show a majority of devs write more TS than plain JS). Lessons should briefly flag which features are plain JavaScript (exist at runtime, e.g. arrow functions, `import`/`export`, array methods) vs TypeScript-only (vanish at compile time, e.g. `: type` annotations, `interface`). Avoid building a separate "learn JS first" track.
- Lessons happen in this repo (`learning-typescript`) via the `teach` skill workspace
- Keep pace deliberate — confirm understanding before layering new syntax

## Out of scope
- Deep build-tooling/config topics (tsconfig internals, bundler setup) until core language fundamentals are solid
- Framework-specific TypeScript (React/Node typings) until the basics of the type system and common JS patterns (modules, async, generics) are comfortable — this is the explicit "next stack layer" once fundamentals land
