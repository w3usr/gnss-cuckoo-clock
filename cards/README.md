# cards/

The punched-card path from SPL source to the clock controller.

- **Encoding spec**: how SPL is laid out on 80-column cards, with per-card sequence numbers,
  checksums, and the run ID that traces a deck to its translation record.
- **Punch** (lead: mechatronics): the microcontroller-driven punch, its die actuation, card
  feed, and registration, with guards and an interlock on the dies.
- **Reader** (lead: EE): the optical or mechanical reader, checksum validation, and the stream
  into the controller.

The Teletype's paper tape is the fallback medium if the punch or reader slips.
