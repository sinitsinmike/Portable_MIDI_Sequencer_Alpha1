# Alpha 7 Release Notes (EN)

## Overview
Alpha 7 is the first stable release focused on reliability, safe data transfer, and predictable behavior.

Main goals:
- stability
- overflow protection
- MIDI compatibility (Type 0 / Type 1)
- sustain support

---

## Key Changes

### Project Buffer
- Before: 16 KB
- Now: 24 KB (24576 bytes)

➡️ Result:
- more events
- fewer overflows
- stable large projects

---

### Event Capacity
- Before: ~500 events per project
- Now: up to 1024 events per track

⚠️ Limit:
- hard limit 1024 per track (Alpha 7 safety)

---

### Upload System Rewrite
- chunked HEX transfer
- packet delays
- READY / DONE handshake
- timeouts

➡️ Fixed:
- device freezes
- broken transfers

---

### Overflow Protection
Added:
- BIN size validation
- per-track event limit

If exceeded:
- upload cancelled
- error logged

---

### MIDI Type 0 Fix
Previously:
- device freeze

Now:
- proper parsing
- channel distribution
- safe limits

---

### Sustain (CC64)
Added full support:
- recording
- playback
- MIDI import/export

---

### Transpose
Global transpose:
- applied during playback
- safe range

---

### Stability Improvements
- freeze fixes
- better error handling
- improved logging

---

## Breaking Changes

- 1024 events per track limit introduced
- Large MIDI files are now rejected
- Type 0 behavior changed (safe parsing)

---

## Alpha 7 Limitations

- No support yet for:
  - pitch bend
  - mod wheel
  - time signature (4/4 only)
- Fixed event size (8 bytes)
- No shared event pool

---

## Roadmap → Alpha 8

### 1. Long Track Mode
- single track uses full memory
- ideal for piano / solo recording

### 2. Event Pool
- shared memory pool
- dynamic allocation

### 3. Event Optimization
- 8 bytes → ~5–6 bytes
- higher capacity

### 4. Extended MIDI
- mod wheel
- pitch bend
- more CC support

---

## Summary

Alpha 7 is a stable foundation:
- reliable upload
- safe behavior
- sustain support
- increased buffer

Foundation for Alpha 8.
