# Lesson 3 complete — arrow functions, modules, array methods, and the "types don't stop runtime" gotcha

The user completed Lesson 3 (arrow functions, `import`/`export`, `.map()`/`.filter()`) and demonstrated real understanding by running the exercise in the TS Playground, hitting a `task.donee` typo, and reasoning about the result. They correctly absorbed the key insight that **a TypeScript type error does not stop the transpiled JavaScript from running** (the Playground still ran it; `!undefined` is always truthy, so `.filter()` returned everything) — and articulated the real-world implication themselves: `tsc`/editor catches this at compile time, before code ships.

## Implications
- Floor is now set: arrow functions, modules, and the two workhorse array methods are understood and can be assumed in future lessons.
- The compile-time-vs-runtime mental model (TS erased before JS runs) is landing well — the JS/TS tag convention is working. Keep using it.
- Next: Lesson 4 on `async`/`await` + `Promise<T>` (per MISSION roadmap). This is also the user's first real encounter with a generic (`Promise<T>`), so it doubles as a gentle on-ramp to the "what's the placeholder for?" generics goal.
