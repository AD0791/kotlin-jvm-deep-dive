# Writing style for this course

This course is written to read like a person wrote it — somewhere between a university paper and a
well-edited programming blog. If you contribute or edit a chapter, hold to these rules.

## Voice

- **Paragraphs, not bullet dumps.** A concept gets prose that states it, motivates it, and works
  through the *why* in connected sentences. Use a bullet list only for genuinely parallel items, and a
  table only for a real reference matrix a reader will scan. If a bullet list is "term — definition,
  term — definition," rewrite it as prose.
- **One idea per paragraph, then build on it.** Sections read as an argument with a throughline, not a
  pile of sealed topics. Connect paragraphs: "we did X above, which is why Y is now possible."
- **Vary the rhythm** — sentence length, paragraph length, and chapter length. Let a chapter be as
  long as its material needs. Uniformity reads as machine-made.
- **Second person, for an experienced programmer new to Kotlin.** Assume JS/Node and Python; spend
  words on what's actually new (the JVM, the type system, coroutines, the build tools).
- **Authorial voice is welcome** — an honest opinion, a small real gotcha, a "here's the wrong way
  first, and why." Never invent an anecdote.

## Don't

- No `> **Goal:**` openers. Open on a problem, a question, or a scene.
- No `## Recap` bullet-dumps or a `**Sources:**` label. Close with a short synthesis that points
  forward; fold sources into inline links plus at most a one-line "Further reading."
- No bold on every other phrase. Bold is for a load-bearing term on first use.
- No filler tics: "memorize this," "hold that thought," "this is the payoff," "every token matters."
- No identical numbered `## 1. / ## 2.` skeleton across chapters. Use headings that name the idea.

## Do

- **Every chapter carries one worked example that grows** — start minimal, complicate it, then connect
  it to the real `core`/`server`/`app` code. Model: the `menu { }` DSL in
  [04 · Functions, lambdas & DSL](04-functions-lambdas-dsl.md).
- **Keep the verified material exact** — REPL-checked snippets, real `javap` output, diagrams, and the
  cross-links between chapters. Don't rename a heading a link targets without fixing the link.
- **Keep tying concepts to the running app** — that through-line is the course's spine.
