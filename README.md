# STRATA
### Multi-Layer Arrangement Engine

A Kontakt instrument for real-time loop-based arrangement performance.
Four synchronized layers — Drums, Bass, Top Line, Wildcard — all tempo and key locked,
designed to be stacked and performed live.

---

## Concept

STRATA lets performers build full musical arrangements on the fly by combining
pre-recorded loops across four categorical layers. Each layer has multiple loop
options and independent playback modes, creating an experience closer to a
looper pedal than a traditional sample library.

**Reference instruments:** Heavyocity Symphonic Destruction, Heavyocity Damage 2.
**What STRATA adds:** four distinct musical layers, all synchronized, all performable live.

---

## Architecture

```
4 Channels:  DRUMS / BASS / TOP LINE / WILDCARD
Per Channel: 3 Slots (A, B, C) — each holds a different loop simultaneously
Per Slot:    8 loop options, navigable via arrow keys
             FREE mode — plays while key held, stops on release
             HOLD mode — latches on press, stops on second press
             Bar sync  — HOLD mode starts align to next bar boundary
```

---

## Project Structure

```
STRATA/
├── Scripts/          KSP scripts for each milestone
├── Instruments/      Kontakt .nki files (not tracked in git)
├── Samples/          Audio content (not tracked in git)
├── UI/               HTML mockups of the instrument interface
└── Docs/             Functional and technical specifications
```

---

## Milestone Progress

| Milestone | Description | Status |
|---|---|---|
| M1  | 4-channel basic triggering | ✅ Complete |
| M2a | FREE mode (gated) + HOLD mode (latch) | ✅ Complete |
| M2b | Bar-boundary sync for HOLD mode | ✅ Complete |
| M3  | Loop navigation (8 loops per channel) | 🔄 In Progress |
| M4  | Energy levels (5 intensity variations) | ◻️ Pending |
| M5  | 3 slots per channel (A / B / C) | ◻️ Pending |
| M6  | Scenes + DISCOVER randomization | ◻️ Pending |
| M7  | Full custom UI | ◻️ Pending |

---

## Key Design Decisions

- **FREE vs HOLD:** FREE = gated (plays while held). HOLD = latch (loops until stopped).
- **Bar sync:** Two-press — queue on first press, confirm on second press at bar boundary.
- **MIDI triggers:** Notes 50/55/60/65 (D2/G2/C3/F3). Mode toggles at 48/52/57/62.
- **Aesthetic:** Neve/API vintage console, warm brushed aluminum, vertical channel strips.

---

## Development Environment

- **Platform:** Native Instruments Kontakt 7 Full
- **Scripting:** KSP (Kontakt Script Processor)
- **Code editor:** Cursor
- **DAW:** Logic Pro
