# AI Usage Log: GNSS-Disciplined Cuckoo Clock

A project of the University of Scranton Amateur Radio Club (W3USR).

This log records every substantive AI-assisted session for "GNSS-Disciplined Cuckoo Clock:
An Interdisciplinary Senior Design Project".

Required by the University of Scranton AI Policy, the HamSCI Generative AI Use Agreement,
and NASA and NSF guidance on generative AI in funded research. The project is unfunded.
See `.claude/rules/ai-governance.md`.

Entries are appended newest at the bottom, and the `/commit` command writes them for you.

---

## Entry format

```
## [YYYY-MM-DD HH:MM TZ]
- **Tool**: Claude (Anthropic), <exact-model-id>
- **Session Purpose**: What this session set out to do
- **Sections/Files Affected**: The specific files or documents touched
- **Nature of Contribution**: Draft / Edit / Analysis / Code generation / Research / Scaffolding
- **Human Review Status**: Reviewed and verified / Partially reviewed / Pending review
- **Git Hash**: Filled in after committing
```

Date and time come from the system clock via `date`, never from an estimate. The Tool field
carries the actual running model ID.

---

<!-- Append new entries below this line, newest at the bottom. -->

## [2026-10-29 02:34 UTC]
- **Tool**: Claude (Anthropic), claude.ai web chat, claude-opus-5-5
- **Session Purpose**: Draft the project description for an interdisciplinary senior design
  project building a GNSS-disciplined cuckoo clock, then extend it at NAF's direction: Teletype
  Model 33 console, WWV/WWVB secondary reference, hourly Morse announcement, Nixie display,
  budget, safety, instrumentation, and AI-use policy sections, a Shortt-Synchronome
  free-pendulum movement, and multi-constellation GNSS in place of GPS.
- **Sections/Files Affected**: `docs/project-description.html` (also kept as a Claude Doc in
  claude.ai and published at https://claude.ai/artifact/NvzpvZ8yYe893bFaivyaNs)
- **Nature of Contribution**: Draft and edit; architecture and timeline diagrams drawn as inline SVG
- **Human Review Status**: Partially reviewed
- **Git Hash**: Filled in after committing

## [2026-10-29, time not recorded]
- **Tool**: Google Gemini image generation ("Nano Banana"), exact model version not recorded
- **Session Purpose**: Generate the four illustrations used on the project page; the opening
  illustration was regenerated and refined over several edit passes using prompts drafted in
  claude.ai (see next entry).
- **Sections/Files Affected**: `docs/figures/*.jpg`, figures inlined in `docs/project-description.html`
- **Nature of Contribution**: Image generation. Illustrations are artistic depictions, not
  engineering drawings; they do not show the actual build.
- **Human Review Status**: Reviewed by NAF for depiction of project elements
- **Git Hash**: Filled in after committing

## [2026-10-29 13:38 UTC]
- **Tool**: Claude (Anthropic), claude.ai web chat, claude-opus-5-5
- **Session Purpose**: Draft and critique image-generation prompts for the opening
  illustration so it shows the Shortt master and slave, ASR-33, card reader, punch cards, and
  GNSS/WWV chain; swap the final image into the published project page; prepare the handoff
  bundle for instantiating the project from `w3usr/ai_project_template`.
- **Sections/Files Affected**: `docs/project-description.html` (opening figure, caption, alt
  text), `docs/figures/`, `HANDOFF.md` and `ai/handoff_log_entries.md` (handoff files, not committed)
- **Nature of Contribution**: Edit and scaffolding
- **Human Review Status**: Pending review
- **Git Hash**: Filled in after committing

## [2026-10-29 13:55 UTC]
- **Tool**: Claude (Anthropic), claude-opus-5-5
- **Session Purpose**: Instantiate the GNSS-Disciplined Cuckoo Clock project from
  `w3usr/ai_project_template` using the claude.ai handoff bundle: fill placeholders, record
  visibility (public) and license (MIT code, CC BY 4.0 docs), create subsystem folders, write
  the project README, record the template commit, and draft a rule file for the AI Rust-to-SPL
  translator.
- **Sections/Files Affected**: `CLAUDE.md`, `README.md`, `LICENSE` (MIT), `NOTICE`,
  `docs/LICENSE` (CC BY 4.0, moved from root), `.gitignore`, `.claude/template.json`,
  `.claude/rules/ai-governance.md` (funder, project-specific constraints),
  `.claude/rules/ai-translator.md` (new, draft), `ai/ai_usage_log.md` (reset; handoff entries
  added), `docs/project-description.html` (AI disclosure footer), `docs/figures/` (added from
  handoff), `firmware/`, `translator/`, `spl/`, `cards/`, `hardware/`, `test/` (READMEs)
- **Nature of Contribution**: Scaffolding and draft; names, visibility, license, funder, and
  review statuses as directed by NAF
- **Human Review Status**: Pending review (`ai-translator.md` is explicitly a draft for review in the PR)
- **Git Hash**: Filled in after committing
