# ViRa_V1.0 bring-up checklist

Order matters: prove the low-voltage side works on bench power **before** the
board ever sees mains.

## 1. Bare board, no mains

- [ ] Visual: no solder bridges on U3 / U5 / U2, relay orientation matches silk.
- [ ] Continuity: `GND` to `+5V` and `GND` to 3V3 rail — must **not** be shorted.
- [ ] Mains-to-SELV: confirm no continuity between J1 pads and any low-voltage
      net. This is the isolation barrier; check it before anything else.

## 2. Low-voltage rails, bench supply on the 5 V rail (no mains, U1 not fitted)

- [ ] Inject 5 V at TP4. Measure TP3 = 3.3 V ±5 % (AMS1117 output).
- [ ] Idle current sane (tens of mA, not hundreds).
- [ ] ESP32-S3 enumerates over USB-C; flash a blink sketch.

## 3. Peripherals (still no mains)

- [ ] Buzzer LS1 on GPIO1 — tone.
- [ ] Status LEDs D1/D5/D6.
- [ ] DS3231M over I2C (GPIO8 SDA / GPIO9 SCL) — read time, confirm BT1 keeps it
      across a power cycle.
- [ ] Buttons: SW1 = reset, SW2 = boot. SW3-SW6 read on GPIO11/12/13/14
      respectively (active low, 10k pull-ups R13-R16).
- [ ] Relay: drive GPIO2 high, hear K2 click, confirm continuity J1.3 ↔ J1.4.
      Do this with a multimeter on the contacts, not with a load.

## 4. Mains — only after all the above passes

Do not perform this step without an isolation transformer, an RCD, and
appropriate training. The board has an unresolved 2.10 mm mains-to-SELV gap at
the relay (see the project README); it is not suitable for connection to mains
as built.

## Known issues to check against

- Mains-to-SELV minimum is 2.10 mm at K2's mains COM pad.
