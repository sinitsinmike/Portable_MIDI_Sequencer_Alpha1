# Alpha1 Workflows (EN)
Portable MIDI Sequencer — Public Alpha 1

---

## 1. Overview
This document describes **how Alpha1 is used in practice**, focusing on:
- Recording workflows
- Live behavior
- Menu and edit logic
- Real-time constraints

It complements the User Manual and Quick Reference.

---

## 2. Linear Recording Workflow

```
[STOP]
  |
  | set BPM / Track / Mode = Linear
  v
[REC pressed]
  |
  | 4-beat count-in
  v
[RECORDING]
  |
  | MIDI events recorded once along timeline
  | Metronome active
  |
[STOP]
  |
  v
[PLAY]
```

### Notes
- Recording is **destructive per track**
- Re-recording a track overwrites previous content
- Track = MIDI channel (1–16)

---

## 3. Loop Recording Workflow

```
[STOP]
  |
  | set Mode = Loop
  | set Loop Length
  v
[REC pressed]
  |
  | 4-beat count-in
  v
[LOOP RECORDING]
  |
  | overdub enabled by default
  | loop wraps automatically
  |
[STOP]
```

### Loop-specific behavior
- Recording is **non-destructive (overdub)**
- Pressing REC during recording clears current track instantly
- FF / REW switches tracks without stopping
- Hanging notes possible near loop boundary (use MIDI panic)

---

## 4. Menu & Edit Workflow

```
Root Screen
  |
  | Encoder press
  v
Edit Mode (*)
  |
  | Encoder rotate
  v
Change value
  |
  | Encoder press
  v
Apply / Exit Edit
```

### Editable items
- BPM (Stop mode only)
- Track
- Sequencer mode
- Loop length
- Quantize
- Save / Load / Clean

---

## 5. Record-Time Restrictions

During recording, the following are blocked:
- Save / Load / Clean
- Loop length edit
- Sequencer mode change

This prevents breaking live performance flow.

---

## 6. Track Switching Logic

### Encoder-based
- Enter edit on Track field
- Select desired track number

### Button-based (recording only)
- FF → Track +1
- REW → Track -1

Immediate response, no confirmation required.

---

End of document.
