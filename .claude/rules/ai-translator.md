---
paths:
  - "translator/**"
  - "spl/**"
  - "cards/**"
---

# AI Translator Rules
*Draft for project lead review. Proposed 2026-10-29; not yet approved.*

This project uses AI in two different ways, and they are governed differently:

| Use | Example | Governed by |
|---|---|---|
| **AI as a development aid** | A student uses Claude Code to write the differential test harness, or the punch driver | `ai-governance.md`: one entry per session in `ai/ai_usage_log.md` |
| **AI as a subsystem** | The translator sends the Rust reference to a model and gets SPL back | This file: one run record per translation, kept with the translator |

The translator's output goes into the clock itself, onto cards, and into the graded result. It
is trusted only once it has been tested, and its provenance is recorded for every build.

## The Rust Reference Is the Specification
- The Rust code in `firmware/` defines correct behavior. The translator converts it; it does
  not reinterpret it. A translation that "improves" on the reference is a wrong translation.
- Expected outputs for the differential tests come from **running the Rust reference**, never
  from a model. AI does not write, edit, or regenerate test vectors or expected outputs.
- AI does not edit the differential test harness, the test vectors, or the pass criteria in
  the same change that makes a translation pass. A harness change is its own PR, reviewed on
  its own merits.

## Run Records
Every translation run, passing or failing, produces a record committed under
`translator/runs/`. Each record holds:

| Field | Requirement |
|---|---|
| **Run ID and time** | From the system clock, UTC. Never estimated. |
| **Model** | Provider and exact model ID as the API reported it (not an alias such as "latest"), plus sampling parameters |
| **Prompt** | The prompt template's path and git hash under `translator/prompts/`, so the exact prompt can be recovered |
| **Input** | Git hash of the Rust source translated |
| **Output** | Path and SHA-256 of the SPL produced |
| **Harness result** | Test vector set and its version, pass/fail per vector, and the first divergence on a failure |
| **Human edits** | Any hand edit to the SPL after translation, who made it, and why |

Failed translations are kept, not discarded. What the harness caught is a project result in
its own right and feeds the final report.

## The Punch Gate
Nothing is punched, written to paper tape, or loaded into the controller unless:

1. The harness has run on **the exact SPL file** being punched (same SHA-256), and
2. It matches the Rust reference on **every** recorded test vector, and
3. The SPL listing has been printed or otherwise reviewed by a person, who signs off in the
   run record.

A hand edit to the SPL after translation sends it back through the harness. The punched deck
carries the run ID (in a header card or the sequence field) so any deck traces back to its
record. The control law itself must live in SPL, not in the C or Rust I/O shim.

## Credentials and Data
- The repository is public. The translator's API key lives in a gitignored `.env` and is never
  committed. Use a key belonging to the project, as decided by the project lead, not a
  student's personal key.
- Only this project's own code and recorded test data go to the model. Nothing confidential,
  export-controlled, or belonging to someone else.

## Disclosure
- The final report, any poster or paper, and the public demo state that the clock's control
  program was machine-translated from Rust to SPL by a named model, with the model IDs used,
  and summarize the harness results including failures.
- Credit stays human: students are credited for the reference implementation, the translator
  tooling, the prompts, and the harness. The model is named as a tool, never as an author.
- The `README.md` says that SPL in `spl/` is AI-translated and points to `translator/runs/`.
