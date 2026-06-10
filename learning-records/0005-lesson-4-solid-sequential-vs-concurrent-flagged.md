# Lesson 4 understanding solid; sequential vs. concurrent awaits flagged for later

The user worked through several rounds of restaurant analogies for `Promise`/`async`/`await` and converged on a correct mental model: a Promise is a claim ticket for a value arriving later, `await` only pauses the calling function (not the whole program), and chained `await`s within one async function model a real dependency chain (prep → cook → plate, each step requires the previous to finish).

## Implications
- Core async/await + `Promise<T>` understanding (Lesson 4) is solid — no need to re-teach the basics.
- User explicitly asked to revisit **sequential vs. concurrent awaits** (including `Promise.all`) once they're more advanced, rather than now. This is a natural follow-up to Lesson 4 and ties into the upcoming generics lesson (`Promise.all<T[]>` etc.) — good candidate for a future lesson once generics basics land.
