# Alpha1 MIDI Sequencer  
User Manual — Alpha1 v1.0

---

## 1. Introduction

Alpha1 is a compact hardware MIDI sequencer designed for real-time performance recording and hands-on musical workflows.

It focuses on capturing musical intent through timing, interaction, and flow, rather than graphical editing or pattern construction. Alpha1 records MIDI performances as they are played, emphasizing immediacy, predictability, and reliability in live and studio environments.

Alpha1 is best suited for musicians with a good sense of timing who prefer playing parts live on a MIDI keyboard or pads, rather than programming sequences step by step.

---

## 2. What Alpha1 Is (and Is Not)

### What Alpha1 Is

Alpha1 is:
- A performance-oriented MIDI sequencer
- Designed for real-time recording and playback
- Intended to serve as a centerpiece of a dawless setup
- Optimized for minimal screen interaction and tactile control
- Focused on stability and predictable behavior during recording and playback

Incoming MIDI data is recorded and passed through in real time, allowing musicians to hear their performance immediately through connected sound modules.

---

### What Alpha1 Is Not

Alpha1 is not designed to mimic a desktop DAW workflow or provide graphical MIDI editing.

It does not use:
- Step grids
- Piano-roll views
- Pattern-based sequencing
- Visual note editing or timeline manipulation

There is no concept of drawing notes or editing them graphically on a screen.

Instead, Alpha1 prioritizes:
- Timing
- Musical flow
- Real-time interaction
- Predictable behavior during performance

---

## 3. Hardware Overview

Alpha1 uses a minimal and performance-focused hardware interface.

### Controls

- **8 buttons**, arranged horizontally
- **1 rotary encoder with push button** (SELECT)
- **8 LEDs**, one LED directly above each button

There are no long-press actions in Alpha1. All interactions are based on short presses, encoder rotation, and encoder push.

---

### Button and LED Relationship

Alpha1 uses a one-to-one relationship between buttons and LEDs:
- Each button has a dedicated LED directly above it
- LEDs provide immediate visual feedback about:
  - Playback state
  - Recording state
  - Count-in
  - System status

Track selection and numeric values are displayed on the screen, not indicated by LEDs.

---

### Display

Alpha1 uses a small OLED display intended for status and parameter feedback, not for detailed editing.

The display is used to show:
- Current track number
- BPM
- Sequencer mode (Linear / Loop)
- Menu items (Save / Load / Clean / Quantize)
- Edit state indicator (`*`)

The display does not show graphical representations of MIDI notes, timelines, or patterns.

---

### MIDI Connections

- **MIDI IN (TRS)**
- **MIDI OUT (TRS)**

Standard TRS-to-5-pin DIN adapters can be used to connect external MIDI controllers and sound modules.

Alpha1 is a MIDI sequencer, not a sound generator. To hear sound, an external MIDI sound module or synthesizer must be connected to the MIDI OUT port.

---

## 4. Sequencer Modes

Alpha1 supports two sequencing modes:
- **Linear mode**
- **Loop mode**

The current mode is shown on the main screen as `seq: Linear` or `seq: Loop`.

There are two intentional entry points for switching modes:
- The `seq:` field on the main screen
- The `loop:` field (when loop length is set)

This design allows switching to Loop mode immediately after setting loop length, without navigating back to the root screen.

---

## 5. Recording Process

Recording behavior depends on the selected sequencer mode.

Before recording:
1. Connect a MIDI controller to MIDI IN
2. Connect a sound module to MIDI OUT
3. Set BPM
4. Select a track
5. Select sequencer mode (Linear or Loop)

Pressing the **REC** button arms recording and starts a 4-beat count-in.

During count-in:
- LED and piezo metronome clicks play in sync
- Recording has not started yet

When count-in ends:
- The LED above the REC button lights up
- Actual MIDI recording begins

---

## 6. Linear Mode Recording

In Linear mode, recording is **destructive**.

- Each recording pass replaces the existing content of the selected track
- There is no overdub in Linear mode
- Previously recorded material on the same track is erased when recording starts

Linear mode is suitable for recording complete performances track by track along the timeline.

---

## 7. Loop Mode Recording

In Loop mode, recording is **non-destructive** and defaults to overdub behavior.

- MIDI events are looped based on the selected loop length
- Recording continues indefinitely until STOP is pressed
- New events are overdubbed on the current track

Special behaviors in Loop mode:
- Pressing **REC during recording** immediately clears all MIDI events on the current track
- Track switching is possible during recording:
  - **FF** → next track
  - **REW** → previous track
- This allows live performance-style recording without stopping the loop

---

## 8. Quantization

Quantization in Alpha1 is applied **after recording** (post-factum).

- Global per project
- Available in Stop mode only
- Applies to already recorded MIDI events

Quantization resolution options:
- Quarter notes (1/4)
- Eighth notes (1/8)
- Sixteenth notes (1/16)

There is no step grid or visual editing involved.

---

## 9. Project Management

Alpha1 supports project-based storage in internal flash memory.

Available operations:
- Save Project
- Load Project
- Clean Project

Projects are retained after power loss.

Saving a project also updates the system project, which remembers the last used project number on boot.

---

## 10. User Interface & Navigation

Navigation is performed using:
- Encoder rotation to move between fields
- Encoder push to enter and confirm edit mode

When a parameter is in edit mode:
- An asterisk (`*`) appears on screen
- Encoder rotation changes the value
- Encoder push confirms and exits edit mode

Certain menu items are blocked during recording to prevent accidental interruption:
- Save
- Load
- Clean
- Loop length
- Sequencer mode switch

---

## 11. Metronome and Count-in

Alpha1 provides both visual and audible timing assistance:
- LED metronome active during Play and Record
- Piezo metronome active during Record only
- First beat of the bar is accented with a higher-pitched click

Count-in:
- 4 beats
- Available in Record mode only
- Recording starts only after count-in completes