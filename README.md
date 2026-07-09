# Kotlin, from the JVM up — a deep-dive course

A from-scratch course on Kotlin and the ecosystem it runs on, written while building a real project: a
multiplayer app with a shared pure-Kotlin `core` module, a Ktor WebSocket backend, and a Jetpack
Compose Android app. It's aimed at someone who can already program but is new to Kotlin and the JVM,
and who wants to understand every line rather than just recognize the syntax — what each construct
actually compiles to, why the runtime behaves the way it does, and how the build and the frameworks
fit together underneath.

The one thing that sets it apart is that it doesn't ask you to take anything on faith. Every bytecode
listing is real `javap` output from a compiled class, every snippet with a stated result was actually
run, and every claim about how something behaves is grounded in the official JetBrains, Ktor, Android,
and Gradle documentation and links back to it.

---

## The mental model the whole course builds toward

```mermaid
flowchart TB
    subgraph SRC["Kotlin source — 3 modules"]
        C["core (pure rules engine)"]
        S["server (Ktor + WebSockets)"]
        A["android (Jetpack Compose)"]
    end
    C -->|kotlinc| BJ["JVM bytecode (.class)"]
    S -->|kotlinc| BJ
    A -->|kotlinc| BA[".class"]
    BJ -->|runs on| JVM["A JVM (server / desktop)"]
    BA -->|"D8 → DEX, R8 shrink"| ART["ART (Android Runtime)"]
    GR["Gradle + wrapper — resolves deps, runs kotlinc, packages"]:::t
    GR -.-> SRC
    classDef t fill:#eee,stroke:#999,stroke-dasharray:4 3;
```

---

## Course index

Start at [`kotlin-course/`](kotlin-course/README.md) and read in order the first time through, or jump
to whatever topic you need.

| # | Chapter | You'll understand |
|---|---------|-------------------|
| 00 | [Fast start & whole-stack map](kotlin-course/README.md) | How the pieces fit; how to run everything |
| 01 | [The JVM & bytecode](kotlin-course/01-jvm-and-bytecode.md) | Bytecode, JVM memory, class loading, JIT, GC, DEX/ART |
| 02 | [Kotlin → bytecode (all angles)](kotlin-course/02-kotlin-to-bytecode.md) | What `data class`, `object`, extensions, default args *become* — with real `javap` output |
| 03 | [Language core & the type system](kotlin-course/03-language-core.md) | Null safety, `Any`/`Unit`/`Nothing`, scope functions, `sealed`, generics & variance |
| 04 | [Functions, lambdas & DSLs](kotlin-course/04-functions-lambdas-dsl.md) | Lambda-with-receiver — the idea behind every `{ }` block in Ktor & Compose |
| 05 | [Coroutines & Flow](kotlin-course/05-coroutines-and-flow.md) | Suspension vs blocking, structured concurrency, `Channel`/`Flow`/`StateFlow` |
| 06 | [Gradle & the build ecosystem](kotlin-course/06-gradle-and-ecosystem.md) | Configurations, BOM, version catalogs, the AGP→APK pipeline, Ktor & Compose internals |

Chapters 07–09 take all of the above and apply it to a real codebase, line by line. They live in a
separate private repo, since they walk my in-progress product code — but the six public chapters here
teach every concept those walkthroughs use.

---

## What makes it different

A few choices give the course its character. Chapter 02 disassembles a real compiled class to show the
`data class` machinery, the `object` singleton, the extension-function receiver, and the
default-argument bitmask, so that "Kotlin compiles to bytecode" stops being a slogan and becomes
something you've actually looked at. Nothing is asserted that wasn't checked: results came out of the
Kotlin REPL or the script runner, and every bytecode listing out of `javap -c -p`. The diagrams do real
work rather than decorate — Mermaid flow and sequence diagrams for the compilation pipeline, coroutine
suspend and resume, structured concurrency, the APK build, the WebSocket lifecycle, and Compose's data
flow, plus ASCII layouts for memory and bytecode. And it stays honest about its sources, linking out to
kotlinlang.org, ktor.io, developer.android.com, and docs.gradle.org at the point each claim is made.

## Try the code as you read

The course is best read with a terminal open beside you, running the same three tools it uses
throughout:

```bash
kotlin                       # REPL — paste snippets, see results
kotlinc file.kt -d out.jar   # compile ahead-of-time
javap -c -p Some.class       # disassemble — see the real bytecode
```

---

## About

Written by Alexandro Disla ([GitHub @AD0791](https://github.com/AD0791)) while learning Kotlin by
building a real project, and shared publicly as a learning log and reference — corrections and questions
are welcome via issues.

## License

© 2026 Alexandro Disla. The written content of this course is licensed under
[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE) — you're free to share and adapt
it, with attribution. Code snippets are provided under the same terms; reuse them freely with credit.
