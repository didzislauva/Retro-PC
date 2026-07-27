# BTC 80286 Award BIOS Dumps

Preservation of the original BIOS ROMs from a late-1988 **BTC (Behavior Tech Computer Corp.)** 80286 Baby AT motherboard.

## Motherboard Information

| Item | Value |
|------|-------|
| Manufacturer | BTC (Behavior Tech Computer Corp.) |
| PCB marking | BTC VERSION 1.0R |
| PCB date code | 8212 |
| CPU | AMD N80L286-10/S |
| CPU Frequency | 10 MHz |
| Architecture | Intel 80286 |
| Bus | 16-bit ISA (AT) |
| BIOS | Award Software Inc. |
| BIOS ROMs | HI / LO EPROM pair |
| Chipset | Chips & Technologies CIC83745AZ / CIC83746AZ |
| Keyboard | AT DIN |
| Battery | External battery connector |

## BIOS ROMs

The motherboard uses two interleaved 16-bit BIOS EPROMs:

| File | Position |
|------|----------|
| `286_hi.bin` | High byte |
| `286_lo.bin` | Low byte |

Each EPROM was dumped individually using a **TL866II Plus** programmer.

EPROM type:

- STMicroelectronics M27C256B
- 32 KB each
- UV erasable EPROM

The combined BIOS image is 64 KB after interleaving.

## Dumping Procedure

Hardware:

- XGecu TL866II Plus
- MiniPro 0.7.4

Example commands:

```bash
minipro -p 'M27C256B(2)@DIP28' -r 286_hi.bin
minipro -p 'M27C256B(2)@DIP28' -r 286_lo.bin
```

Each ROM should be read multiple times and compared to verify a stable dump.

Example verification:

```bash
cmp dump1.bin dump2.bin
sha256sum dump*.bin
```

## Board Hardware

### Processor

- AMD N80L286-10/S
- 10 MHz

### Chipset

- Chips & Technologies CIC83745AZ
- Chips & Technologies CIC83746AZ

### Memory

Installed DRAM:

- Mitsubishi M5M4256P-15

Configuration:

- Four RAM banks
- 256K×1 DRAM devices
- Approximately 512 KB installed (board dependent)

### Expansion

- Eight ISA expansion slots
- AT keyboard connector
- External battery connector

## BIOS Vendor

The board uses an original **Award Software Inc. BIOS**, supplied as separate HI and LO EPROMs for the 16-bit data bus.

The BIOS labels contain:

```
286 LO
286 HI
Award Software Inc.
02274219
```

## Estimated Production Date

The motherboard was likely manufactured during late **1988** or early **1989**.

Evidence includes:

- PCB marking: 8212
- Chipset date codes: 8843
- AMD CPU production: late 1988

## Preservation

This repository exists to preserve the original firmware from a BTC 80286 motherboard for historical and restoration purposes.

Original hardware is becoming increasingly scarce, and preserving firmware helps support:

- vintage computer restoration
- hardware emulation
- BIOS research
- archival projects
- retro computing enthusiasts

## License

BIOS images remain the copyright of their original owner (Award Software Inc. and/or the motherboard manufacturer).

This repository is provided solely for historical preservation, research, compatibility testing, and restoration of original hardware.
