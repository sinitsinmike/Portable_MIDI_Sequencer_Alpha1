# Alpha4 – MIDI Clock & Transport Implementation

## Overview

Alpha4 introduces stable and spec-compliant MIDI Clock OUT and Transport OUT implementation.

Supported messages:
- MIDI Clock (0xF8)
- Start (0xFA)
- Stop (0xFC)
- Continue (0xFB)

Transport logic is transition-based and avoids repeated transport spam.

---

## MIDI Clock Output

Internal engine resolution: 96 PPQN  
MIDI Clock resolution: 24 PPQN  
Divider: 96 / 24 = 4

Implementation:

midiClockDivider++;

if (midiClockDivider >= 4) {
    Serial1.write(0xF8);
    midiClockDivider = 0;
}

Clock is sent only when isPlaying == true.

Divider resets on stop.

---

## Transport Output

State tracking in Core1:

static bool lastIsPlaying = false;
static bool lastIsPaused  = false;

bool playing = midiEngine.isPlaying;
bool paused  = midiEngine.isPaused;

---

### START (0xFA)

Sent only when:
playing == true
lastIsPlaying == false
lastIsPaused == false

---

### CONTINUE (0xFB)

Sent only when resuming from pause:

else if (playing && lastIsPaused) {
    Serial1.write(0xFB);
}

---

### STOP (0xFC)

Sent only on transition from playing → stopped:

if (!playing && lastIsPlaying) {
    Serial1.write(0xFC);
}

---

## Behavior Summary

Play from stopped → Start (0xFA)  
Pause → Stop (0xFC)  
Resume → Continue (0xFB)  
Stop → Stop (0xFC)

---

## Architecture

Clock + Transport run on Core1  
UI runs on Core0  
No transport logic inside UI  
No flash operations on Core1  
MIDI Clock independent from UI

---

Alpha4 Code Freeze
