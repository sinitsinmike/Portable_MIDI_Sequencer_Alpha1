# Alpha 7 Feature Overview

## Core Sequencer
- Real-time MIDI sequencing
- Linear mode
- Loop mode
- Real-time recording
- Per-track recording
- Per-track MIDI channel assignment
- 16 tracks, 1024 events per track
- 24 KB project buffer
- Stable transport (play / stop / pause)

## Recording & Looping
- Count-in before recording
- Metronome with accent
- Loop overdub (real-time layering)
- Loop clean (REC during REC)
- Record aligned to bar start
- Real-time MIDI looper workflow

## MIDI Features
- Note On / Note Off recording
- Sustain pedal (CC64) record/playback
- Global transpose
- MIDI Clock out (24 PPQN)
- MIDI Start / Stop / Continue out
- MIDI DIN output

## Performance Controls
- Tap tempo (in stop mode)
- Panic (FF + REW → All Notes Off)
- Live loop layering
- No quantization (WYSIWYG timing)

## Storage
- Chained save system
- Sector-based storage
- Save / Load / Clean project
- Last project restore
- Safe flash handling

## Web Tool
- WebSerial connection
- Export BIN / MIDI
- Import BIN / MIDI
- Type 0 & Type 1 MIDI support
- Upload handshake (READY / DONE)
- Chunked transfer
- Size and overflow protection

## Stability & Safety
- Overdub stable after loop wrap
- Sorted event handling
- No freeze on large MIDI
- Input validation
- All Notes Off safety

## Limitations (Alpha 7)
- 4/4 only
- No pitch bend
- No mod wheel
- No long track mode
- No event pool

## 
- Fixed rotary encoder instability (missed steps, jitter, double steps)
- Implemented correct detent-based decoding (0b11)
- Encoder input is now stable and deterministic