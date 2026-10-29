# translator/

The AI Rust-to-SPL translation stage and the differential test harness that decides whether a
translation is trusted.

- `prompts/`: versioned prompt templates.
- `runs/`: one record per translation run, passing or failing.
- The harness runs the Rust reference (`../firmware/`) and the SPL output on identical recorded
  phase-error sequences and requires matching outputs before anything is punched.

AI here is a subsystem, not only a development aid. `../.claude/rules/ai-translator.md`
governs run records, the punch gate, and disclosure. Lead discipline: CS.
