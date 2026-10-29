# GNSS-Disciplined Cuckoo Clock

*An interdisciplinary senior design project of the University of Scranton Amateur Radio Club (W3USR)*

![A wood-paneled den at night: a cuckoo clock with Nixie tubes, its slave pendulum wired to a copper vacuum tank holding the free master pendulum, a Teletype spilling paper tape, a punched-card reader and cards, and a GNSS antenna feeding a circuit board atop a console shortwave radio.](docs/figures/clock-at-home.jpg)

*Artist's illustration of the finished clock (AI-generated; not an engineering drawing).*

Students build a mechanical cuckoo clock whose timekeeping is disciplined to multi-constellation
GNSS (GPS, Galileo, GLONASS, BeiDou), running control firmware written in the
[Shakespeare Programming Language](https://en.wikipedia.org/wiki/Shakespeare_Programming_Language)
and loaded from punched cards. The cards come from a microcontroller-driven punch, fed by an AI
translation stage that converts a reference implementation written in Rust into SPL.

The project deliberately chains four eras of computing: 18th-century clockwork, 1960s punched-card
media, modern satellite timing, and present-day machine translation of code. The absurdity is
load-bearing. An esoteric target language forces rigorous verification of AI-generated code; a
physical card medium forces real thinking about encoding and data integrity; a pendulum that must
track GNSS to the second forces a real control-loop design.

**The full project description is in [`docs/project-description.html`](docs/project-description.html),
and as a PDF in [`docs/project-description/project-description.pdf`](docs/project-description/project-description.pdf).**

## How it works

- **Build path.** Rust reference → AI translation to SPL → differential test harness (the SPL
  must match the Rust on every recorded test vector) → card punch → card reader → controller.
- **Clock loop.** The controller compares each GNSS pulse-per-second edge with the pendulum's
  optical gate; the SPL program turns that phase error into a period trim.
- **Movement.** A Shortt-Synchronome-style free pendulum: a master pendulum in a sealed,
  partially evacuated tank, impulsed every 30 s, and a slave pendulum driving the cuckoo
  through a hit-and-miss synchronizer. GNSS trims the master through a PI loop wrapped around
  the 1920s mechanical loop.
- **Extras.** WWV/WWVB as a second time reference, a Teletype Model 33 on a 20 mA current loop
  as console, listing printer, and paper-tape fallback, Nixie tubes showing the time and the
  clock's offset, and a Morse code announcement on the hour.

## Repository layout

| Folder | Contents |
|---|---|
| [`firmware/`](firmware/) | Rust reference algorithm, simulator, controller firmware and SPL runtime |
| [`translator/`](translator/) | AI Rust-to-SPL translation, prompts, run records, differential test harness |
| [`spl/`](spl/) | Translated SPL programs that passed the harness |
| [`cards/`](cards/) | Card encoding spec, punch, and reader |
| [`hardware/`](hardware/) | Pendulums and vacuum tank, cuckoo mechanism, Teletype interface, receivers, Nixie display |
| [`test/`](test/) | Timing measurements and analysis |
| [`docs/`](docs/) | Project description, figures, onboarding, AI use agreement |

## Contributing

New to the club's repositories? Start with [`docs/ONBOARDING.md`](docs/ONBOARDING.md), and sign
the Generative AI Use Agreement in [`docs/ai_policy_agreement/`](docs/ai_policy_agreement/)
before using AI tools on this project. Every change goes through a pull request.

## AI use

This repository contains AI-assisted work, and AI is also part of the product:

- The SPL in `spl/` is machine-translated from Rust by a large language model. Each
  translation's model, prompt, and test result are recorded in `translator/runs/`.
- The illustrations in `docs/figures/` were generated with Google Gemini and are artistic
  depictions, not drawings of the actual build.
- The project description was drafted with Claude (Anthropic); review by Nathaniel
  Frissell, W2NAF, is in progress.

[`ai/ai_usage_log.md`](ai/ai_usage_log.md) is the record of every AI-assisted session.

## License

Code is under the [MIT License](LICENSE); documentation in `docs/` is under
[CC BY 4.0](docs/LICENSE). See [`NOTICE`](NOTICE).

Project lead and faculty advisor: Nathaniel Frissell, W2NAF.

73 de W3USR
