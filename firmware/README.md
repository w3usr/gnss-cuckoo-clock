# firmware/

The Rust reference implementation and the clock controller firmware.

- **Reference algorithm**: PPS phase measurement against the pendulum's optical gate, the PI
  loop that trims the master pendulum's rate, holdover behavior, chime scheduling, and the
  hourly Morse encoder. This code is the specification the translator must match.
- **Simulator and test suite**: runs the reference against recorded phase-error sequences and
  produces the expected outputs the differential harness in `../translator/` compares against.
- **Controller and SPL runtime**: the microcontroller board's firmware, the SPL interpreter or
  spl2c-compiled image, and the I/O shim that maps SPL's integer stream onto PPS capture, the
  rate trim, the cuckoo, the Nixie display, and the Teletype console.

Lead discipline: CS (reference), EE and CS (controller). See `../docs/project-description.html`.
