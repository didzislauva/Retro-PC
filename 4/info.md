# Industrial 80286 CPU Board BIOS Dumps

This repository preserves the firmware from a rare late-1980s industrial 80286 Single Board Computer (SBC).

The board integrates CPU, VGA, floppy controller, serial ports, parallel port, keyboard controller, RTC, and memory onto a single ISA backplane CPU card intended for passive industrial backplanes.

---

## Board Information

**PCB markings**

- PWA-286U BD
- ASSY 4116610010

**Processor**

- AMD N80L286-12/S (12 MHz)

**Math Coprocessor**

- Intel D80287-8

**Chipset**

- CHIPS & Technologies NEAT
    - P82C206
    - P82C211B
    - P82C215-12

**Video**

- Paradise PVGA1A-JK VGA
- Analog Devices ADV476KN35 RAMDAC

**Storage Controller**

- Western Digital WD37C65B-PL

**Keyboard Controller**

- Intel P8042AH
- Firmware: MITAC V2.48

---

# BIOS ROMs

The board contains four Texas Instruments TMS27C256-20JL EPROMs.

## System BIOS

Socket | Label
------ | -----
U19 | R12B EVEN
U20 | R12B ODD

The ROMs were successfully dumped and interleaved into a complete 64 KB BIOS image.

### Identification

Phoenix Technologies ROM BIOS

```
Copyright (c) 1985,1986 Phoenix Technologies Ltd.
80286 ROM BIOS Version 3.07
```

Additional strings found:

```
R12B
SYSTEM CONFIGURATION SETUP V1.03
```

Reset vector date:

```
07/30/87
```

---

## VGA BIOS

Socket | Label
------ | -----
U79 | PVGA R05 EVEN
U74 | PVGA R05 ODD

The ROMs reconstruct into a valid Paradise VGA option ROM.

Identified strings:

```
IBM AT COMPATIBILITY - 003056-001
COPYRIGHT PARADISE SYSTEMS INC.
1987,1988
ALL RIGHTS RESERVED
```

Timestamp:

```
07/01/89-11:00:14
```

### ROM Layout

The reconstructed 64 KB image contains:

- 0x0000–0x7FFF : unused / blank
- 0x8000–0xDFFF : valid 24 KB Paradise VGA option ROM
- 0xE000–0xFFFF : unused

The option ROM begins with a valid `55 AA` signature and passes checksum verification.

---

# Dump Verification

Each EPROM was read multiple times using:

- XGecu TL866II Plus
- minipro

Repeated dumps were byte-identical.

Interleaved image SHA-256 hashes:

## System BIOS

```
025c89189cc73ef0f1d8abe439a0fa67d0d9b5a26b1f42721f59c9a60856d33a
```

## VGA BIOS

```
0a4298a53c566d5ad54707abbf88b39996c0dac2010d43d85d40ca43d0810cda
```

---

# Notes

The exact manufacturer of the CPU board has not yet been positively identified.

Current identifying markings include:

- PWA-286U BD
- ASSY 4116610010
- R12B
- MITAC V2.48
- Paradise VGA BIOS 003056-001

If you recognize this board or have documentation, please open an issue or submit a pull request.

---

# License

The ROM images remain copyrighted by their respective owners.

This repository is intended solely for historical preservation, research, repair, and compatibility testing.
