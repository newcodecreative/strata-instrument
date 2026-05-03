# STRATA Changelog

## M2b — Bar-Boundary Sync
**Script:** STRATA_M2b.ksp

### Added
- Bar sync for HOLD mode — loops queue on first press, arm after 4 beats, start on second press
- `%armed[4]` state array for two-press bar sync confirmation
- `%pending[4]` state array for queued starts
- `wait_ticks(3840)` timing (4 beats at 960 ticks/beat)
- Status messages: "queued for bar...", "bar ready - press D2", "started", "stopped"

### Notes
- `play_note` from within `wait_ticks` context does not reliably trigger zones in standard KSP
- Workaround: natural keypress used for zone triggering (two-press confirmation model)
- MIDI trigger notes confirmed: 50 (D2), 55 (G2), 60 (C3), 65 (F3)

---

## M2a — FREE and HOLD Modes
**Script:** STRATA_M2a.ksp

### Added
- FREE mode per channel (gated — plays while key held, stops on release)
- HOLD mode per channel (latch — press to start, press to stop)
- Mode toggle keys: C2(48), E2(52), A2(57), D3(62)
- Per-channel `%ch_mode[4]` state array
- Loop sustain fixed — loop points set in Wave Editor for indefinite looping

### Fixed
- Corrected MIDI trigger note numbers (50/55/60/65 not 26/31/36/41)
- Fixed em-dash encoding issue in KSP comments (use plain hyphens only)
- Resolved loop stopping on key release in FREE mode (suppress note-off in on release)

---

## M1 — Basic 4-Channel Triggering
**Script:** STRATA_M1.ksp

### Added
- 4 channels: DRUMS (D2/50), BASS (G2/55), TOP LINE (C3/60), WILDCARD (F3/65)
- FREE mode toggle (press = start, press again = stop)
- All 4 channels play simultaneously and independently
- Zones mapped in Kontakt Mapping Editor (1 zone per channel)
- Loop mode enabled per zone in Wave Editor
- KSP script: on note / on release callbacks

### Environment
- Kontakt 7 Full running as plugin in Logic Pro
- Note numbering: Kontakt convention (C5=60), so D2=50 not 26
- All KSP variables must be declared in on init (not in callbacks)
- No inline if/then syntax — each if block must use separate lines
- No special characters in KSP (no em-dashes, smart quotes, etc.)
