# hardware/

Everything that moves, and the electronics that tie it together.

- **Movement**: the Shortt-Synchronome-style free master pendulum in its sealed, partially
  evacuated tank (invar rod, 30 s impulse mechanism, rate trim), the slave pendulum and its
  hit-and-miss synchronizer, optical gate sensing, the cuckoo bird and bellows drive, and the
  hour and half-hour strike.
- **Teletype Model 33 interface**: the optoisolated 20 mA current loop to UART adapter (110 baud,
  two stop bits) and its loop supply.
- **References and display**: the GNSS timing receiver, the WWV/WWVB receiver, and the Nixie
  display with its roughly 170 V DC supply.

Safety: interlocks on the punch dies, inspection of the Teletype's mains wiring before
power-up, and enclosure of the Nixie supply, each with a lockout procedure signed off before
unsupervised work.
