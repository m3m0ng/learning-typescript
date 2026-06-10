# TypeScript Cheatsheet

A running, at-a-glance reference. New entries get appended as lessons progress — no need to dig through files.

---

## Lesson 1 — TypeScript Basics

### Reading the syntax

| Pattern | Meaning |
| --- | --- |
| `name: Type` | "`name` must be a value of `Type`" |
| `function f(x: T): R { ... }` | Parameter `x` must be type `T`; the function must return type `R` |
| `let x: T = value;` | Declares variable `x` as type `T` |

### Primitive & common types

| Type | Example value | Notes |
| --- | --- | --- |
| `string` | `"hello"` | Text |
| `number` | `42`, `3.14` | All numbers — no separate int/float |
| `boolean` | `true` / `false` | |
| `T[]` or `Array<T>` | `string[]` | Array where every item is type `T` |
| `void` | — | Function returns nothing useful (used as a return type) |
| `undefined` / `null` | — | Absence of a value |
| `any` | — | "Turn off type checking" — avoid when possible |
| `unknown` | — | Like `any`, but safer — must narrow before use |

### Object shapes: `interface`

```ts
interface User {
  id: number;
  name: string;
  nickname?: string;   // ? = optional property
}
```

A value typed `User` must have `id` and `name`; `nickname` may be omitted.

### Union types: "this OR that"

```ts
type Status = "loading" | "success" | "error";

function describe(value: string | number): string {
  return `The value is ${value}`;
}
```

`type X = A | B` defines a custom alias that can be any one of the listed options.

### Quick mental checklist when reading AI-generated TS

| You see... | Ask yourself... |
| --- | --- |
| `: Type` after a name | "What kind of value is allowed here?" |
| `interface` / `type` | "What shape of object/value does this define?" |
| `?` after a property | "Is this field optional?" |
| `\|` between types | "What are the possible alternatives?" |
| `[]` after a type | "This is a list/array of that type" |

---

## Lesson 2 — Python → TypeScript

### Type names

| Python | TypeScript | Notes |
| --- | --- | --- |
| `int` / `float` | `number` | TS has one numeric type for everything |
| `str` | `string` | |
| `bool` | `boolean` | |
| `list[X]` | `X[]` | "a list/array of X" |
| `None` | `undefined` / `null` | TS has both — don't worry about the difference yet |
| (no return value) | `void` | Used as a function's return type |
| `Any` (typing module) | `any` | Turns off type checking — avoid when possible |

### Variables

| Python | TypeScript |
| --- | --- |
| `x: int = 5` | `let x: number = 5;` |
| `name: str = "Rover-1"` | `const name: string = "Rover-1";` |

Use `const` if the value never changes (most common), `let` if it will be reassigned — like choosing a tuple vs. a regular variable in spirit.

### Functions

```python
def raw_to_voltage(raw: int) -> float:
    return (raw / 1023) * 5.0
```

```ts
function rawToVoltage(raw: number): number {
  return (raw / 1023) * 5.0;
}
```

### Records / structured data

```python
@dataclass
class SensorReading:
    timestamp: int
    sensor: str
    value: float
```

```ts
interface SensorReading {
  timestamp: number;
  sensor: string;
  value: number;
}
```

`interface` = blueprint only, no runtime object — just tells the type checker what shape to expect.

### Lists of records

```python
readings: list[SensorReading] = [...]
```

```ts
const readings: SensorReading[] = [...];
```

### Quick mental checklist when reading AI-generated TS

| You see... | Python equivalent in your head |
| --- | --- |
| `: number` / `: string` / `: boolean` | `: int/float` / `: str` / `: bool` |
| `interface Foo { ... }` | `@dataclass class Foo: ...` |
| `Foo[]` | `list[Foo]` |
| `function f(x: T): R` | `def f(x: T) -> R:` |
| `?` after a property | An optional field — like `Optional[T]` with a default |
| `\|` between types | Like `Union[A, B]` — "could be A or B" |

---

## Lesson 3 — Reading Real TypeScript Files

### JS vs TS at a glance

| Tag | Meaning | Examples |
| --- | --- | --- |
| **JS** | Real syntax — runs at runtime, survives compilation | `const`/`let`, `=>`, `import`/`export`, `.map()`/`.filter()`/`.reduce()`, `if`/loops, `async`/`await` |
| **TS** | Type-only — checked at compile time, then erased | `: number` / `: string` / etc., `interface`, `type` aliases, generic `<T>` parameters |

If you delete every **TS** piece from a `.ts` file, what's left is the JavaScript that actually runs.

### Arrow functions

| Form | Example | Notes |
| --- | --- | --- |
| Block body | `const f = (n: number): number => { return n * 2; };` | Same as `function f(n: number): number { return n * 2; }` |
| Expression body | `const f = (n: number): number => n * 2;` | No braces, no `return` — the expression's value is returned |
| As a callback | `tasks.filter(task => !task.done)` | Most common form — types are usually inferred, not written |

### Array methods you'll see constantly

| Method | Does | Python equivalent |
| --- | --- | --- |
| `arr.map(x => ...)` | Transform every item, return a new array | `[... for x in arr]` |
| `arr.filter(x => ...)` | Keep items where the condition is true | `[x for x in arr if ...]` |
| `arr.reduce((acc, x) => ..., start)` | Combine all items into one value | `functools.reduce(...)` / a running-total loop |
| `arr.find(x => ...)` | First item matching the condition (or `undefined`) | `next((x for x in arr if ...), None)` |

### Modules

| Syntax | Meaning | Python equivalent |
| --- | --- | --- |
| `export interface Foo { ... }` | Make `Foo` usable from other files | Defining `Foo` in a module others can import |
| `export const f = (...) => ...` | Make function `f` usable from other files | A top-level function others can import |
| `import { Foo } from "./types"` | Bring in `Foo` from local file `types.ts` | `from .types import Foo` |
| Not exported | Private to that file | A name not in `__all__` / module-private convention |

### Quick mental checklist when opening a real `.ts` file

| You see... | Read it as... |
| --- | --- |
| Top-of-file `import` lines | "This file depends on these other files/packages" |
| `export` in front of something | "Other files can use this" |
| `const x = (...) => ...` | A function named `x` (arrow function) |
| `arr.map(...)` / `.filter(...)` | A list comprehension over `arr` |
| `: SomeType` anywhere | A guardrail — would vanish if compiled to JS |

### Gotcha: type errors don't stop the JS from running (in the Playground)

The TS Playground transpiles and runs the JS even when there are type errors — it just shows the error alongside the output. A typo'd property (e.g. `task.donee` instead of `task.done`) becomes `undefined` at runtime, so `!task.donee` is always `true` and silently breaks logic like `.filter()`.

In a real project, `tsc` (or your editor's type checker) would flag this **before** the code ever runs — that's the whole point of compiling first.
