# Alpha1 — Quick Reference v1.0 (Public Alpha)

Portable MIDI Performance Sequencer  
Version: Alpha1  
Status: Feature-frozen (Alpha)

---

## 1. Purpose & Intended Use

Alpha1 is a **performance-oriented MIDI sequencer** designed for musicians who prefer **playing MIDI parts live** rather than programming them step-by-step.

It is best suited for musicians with a **good sense of timing** and familiarity with MIDI keyboards or drum pads.

Alpha1 is designed for **DAWless setups** and does not require a computer to operate.

---

## 2. What Alpha1 Is Not

Alpha1 is **not designed to mimic a desktop DAW workflow** or provide graphical MIDI editing.

It does not use:
- Step grids
- Piano-roll views
- Pattern-based sequencing
- Visual note editing or timeline manipulation

There is no concept of “drawing notes” on a screen.

Instead, Alpha1 prioritizes:
- Timing
- Musical flow
- Real-time interaction
- Predictable behavior during performance

---

## 3. Hardware Overview (Quick)

- 8 buttons (numbered 1–8)
- 8 LEDs (one LED directly above each button)
- Rotary encoder with push button (SELECT)
- 0.96" OLED display (I2C)
- Piezo buzzer (metronome / count-in)
- MIDI IN (TRS)
- MIDI OUT (TRS)
- Internal clock (MIDI Clock planned)

There are **no long-press actions** in Alpha1.  
All actions are immediate.

---

## 4. Button & LED Mapping (Quick)

### Buttons
| Button | Function (Primary) |
|------|--------------------|
| 1 | PLAY / STOP |
| 2 | PAUSE |
| 3 | REC |
| 4 | REW |
| 5 | FF |
| 6 | Reserved |
| 7 | Reserved |
| 8 | SHIFT / TAP TEMPO |

### LEDs
- Each button has a dedicated LED above it
- LEDs indicate:
  - Playback state
  - Recording state
  - Count-in progress
  - System status

> Active track indication is shown on the display, not via LEDs.

---

## 5. Display Usage

The OLED display is intended for **status and parameter feedback**, not detailed editing.

The display is used to show:
- Current track number
- BPM
- Sequencer mode (Linear / Loop)
- Menu items (Save / Load / Clean / Quantize)
- Edit state indicator (`*`)

There is **no graphical representation** of MIDI notes or timelines.

---

## 6. Encoder & Edit Logic

- Rotate encoder → navigate values or menu items
- Press encoder → enter / confirm edit
- Edit mode is indicated by `*` on screen
- Press encoder again to confirm and exit edit mode

Some parameters are editable **only in Stop mode**.

---

## 7. Sequencer Modes

### Linear Mode
- Destructive recording
- Recording replaces content of the selected track
- Intended for linear performance recording
- Metronome (LED + piezo) assists timing

### Loop Mode
- Non-destructive recording (overdub by default)
- Loop length must be set before recording
- Recording loops continuously until stopped

Two entry points exist intentionally:
- `Seq: Linear / Loop`
- `Loop: On / Off`

This allows switching to Loop mode quickly after setting loop length.

---

## 8. Recording Behavior

### General
- REC arms recording
- 4-beat count-in starts immediately
- Recording begins after count-in
- LED above REC lights when actual recording starts

### Linear Mode
- Recording is destructive
- Re-recording a track overwrites previous content

### Loop Mode
- Recording is overdub by default
- Pressing REC during recording:
  - Immediately clears all MIDI events on the current track
- Loop wraps automatically at loop length

### Track Switching During Recording
- REW → Track N − 1
- FF → Track N + 1
- Track switching is immediate
- Track number = MIDI channel number (1:1 mapping)

---

## 9. Metronome & Count-In

- LED metronome is active during Play and Rec
- Piezo metronome:
  - Active only in Record mode
  - First beat is accented with higher pitch
- Count-in:
  - Always 4 beats
  - Only in Record mode

---

## 10. Panic & Safety

- FF + REW pressed together:
  - Sends MIDI All Notes Off (panic)
- Useful for hanging notes in Loop mode

---

## 11. Quantize (Post-Factum)

Quantize is a **simple post-recording utility**.

- Global (per project)
- Available in Stop mode only
- Applies to already recorded MIDI events
- Quantization resolution:
  - Quarter notes (1/4)
  - Eighth notes (1/8)
  - Sixteenth notes (1/16)
- No step grid or visual editing involved

---

## 12. Project Management

### Save
- Menu → Save
- Select project number
- Confirm with encoder

### Load
- Menu → Load
- Select project number
- Confirm with encoder

### Clean
- Menu → Clean
- Clears selected project

Projects are stored in flash memory and persist after power-off.

---

## 13. Recording-Time Restrictions

During recording:
- Save / Load / Clean are disabled
- Loop length editing is disabled
- Sequencer mode switching is disabled

This is intentional to prevent accidental interruption of performance.

---

## 14. MIDI Routing Model

- Track number = MIDI channel number
- Up to 16 tracks / 16 MIDI channels
- Requires external MIDI sound module to produce sound
- Incoming MIDI is passed through in real time while recording

---

## End of Quick Reference v1.0