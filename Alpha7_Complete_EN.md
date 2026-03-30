# Alpha 7 — Complete Overview

## What Alpha Is

Alpha is a hardware MIDI sequencer built for musicians who prefer to **play**, not program.

There is no piano roll, no step grid, and no visual editing.  
Everything is based on **real-time performance, timing, and interaction**.

Alpha behaves more like an **instrument** than a traditional sequencer.

---

## Core Concept

- Real-time MIDI recording
- What you play is what you get (no hidden quantization)
- Track = MIDI Channel (1:1 mapping)
- No routing, no menu diving
- Immediate response, predictable behavior

---

## Interface & Interaction

- 8 buttons + LEDs
- Encoder with push
- OLED display (status only)

No long presses.  
All actions are immediate.

LEDs indicate:
- Play / Stop state
- Count-in
- Recording start

---

## Transport & Recording

Recording is a two-stage process:

1. Press REC → playback starts + count-in
2. After 4 beats → recording begins (REC LED turns on)

- Recording always starts **after count-in**
- This ensures predictable timing and performance readiness

---

## Sequencer Modes

### Linear Mode
- Destructive recording
- Re-record replaces track content

### Loop Mode
- Overdub by default
- Loop repeats continuously

Features:
- REC during REC → clears current track
- Track switching during recording (FF / REW)
- Seamless loop wrap

---

## Loop System

- Adjustable loop length (beats per loop)
- Loop wraps automatically

---

## MIDI Features

- MIDI IN / OUT
- Sustain (CC64)
- Global transpose
- MIDI Clock (24 PPQN)
- MIDI Start / Stop / Continue

---

## Performance Features

- Tap tempo (Stop mode)
- Panic (FF + REW → All Notes Off)
- Live loop layering

---

## Storage System

- Chained save
- 24 KB project buffer
- Save / Load / Clean

---

## Web Tool

- Import / Export MIDI
- Type 0 & Type 1 support
- Chunked transfer
- Overflow protection

---

## Stability

- No freeze on large MIDI
- Overdub stable

---

## Limitations (Alpha 7)

- 4/4 only
- No pitch bend
- No mod wheel

---

## Roadmap (Alpha 8)

- Long Track Mode
- Event Pool
