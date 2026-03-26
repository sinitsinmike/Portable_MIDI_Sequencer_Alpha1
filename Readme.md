<img width="985" height="438" alt="Portable_MIDI_Sequencer_Schematics" src="https://github.com/user-attachments/assets/b6c4f1e8-5b15-4b8b-938c-43f01f47feee" />


# Alpha1 — Portable Hardware MIDI Sequencer (Public Alpha)

Alpha1 is a compact, performance-oriented hardware MIDI sequencer
designed for DAWless setups, real-time recording, and tactile musical interaction.

Alpha1 records live MIDI performances, routes up to 16 MIDI channels,
and operates completely without a computer.
It emphasizes timing, immediacy, and predictable behavior,
rather than graphical editing or screen-driven workflows.

This repository contains documentation, firmware binaries,
and supporting materials for the Alpha1 Public Alpha release.

---

## Project Status

🔹 Status: Public Alpha (Alpha1)  
🔹 Intended use: DIY / evaluation / live performance  
🔹 Development stage: architecture and workflow frozen for Alpha1  

Alpha1 is under active development.
Hardware and firmware may change in future Alpha or Beta releases.

---

## What Alpha1 Is

- A standalone hardware MIDI sequencer
- Designed for recording live MIDI performance
- Supports:
  - Linear and Loop sequencing modes
  - Multi-track recording (up to 16 tracks)
  - A strict **1 track = 1 MIDI channel** relationship
- Can serve as the centerpiece of a DAWless setup
- Requires:
  - A MIDI controller (keyboard / pads) connected to MIDI IN
  - An external sound module or synthesizer connected to MIDI OUT

---

## What Alpha1 Is Not

Alpha1 is not designed to mimic a desktop DAW workflow
or provide graphical MIDI editing.

It does not use:
- Step grids
- Piano-roll views
- Pattern-based sequencing
- Visual note drawing or timeline manipulation

There is no concept of “drawing notes” or editing them on a screen.

Instead, Alpha1 prioritizes:
- Timing
- Musical flow
- Real-time interaction
- Predictable behavior during performance

---

## Documentation

This repository includes a complete documentation set:

📘 Documentation:
- Quick Reference (EN / RU)
- User Manual (EN / RU)
- Workflows (Linear / Loop / Menu)
- ASCII State Diagram
- Future Features & Roadmap

All documents are provided in **PDF** and **Markdown** formats.

---

## Firmware

- Firmware is provided as a **UF2 binary**
- Flashed using the standard RP2040 bootloader
- **Source code is not published or distributed**

---

## Hardware

- Open hardware schematics
- Intended for DIY assembly
- Schematics are provided
- Fully assembled devices are not sold as part of Alpha1

---

## License Summary (Important)

This project is distributed under a custom user license.

You are allowed to:
- Build the device for personal use
- Use it for music creation and live performance
- Perform and earn money using the device
- Modify the hardware for personal use

You are **not** allowed to:
- Manufacture devices for sale
- Sell derivative hardware products
- Redistribute the firmware or its copies

📄 See `LICENSE.md` for the full license text.

---

## Alpha Disclaimer

Alpha1 is an experimental release intended for:
- Workflow evaluation
- Real-world musical testing
- Focused user feedback

The project is provided **“as is”**, without warranties of any kind.

---

## Feedback

If you encounter a bug, unexpected behavior, or have a focused suggestion related to Alpha1:

Please use the standard GitHub workflow to report it.

1. Go to the **Issues** tab of this repository
2. Click **New Issue**
3. Provide a clear and detailed description, including:
   - What you were doing
   - What you expected to happen
   - What actually happened
   - Any relevant context (mode, project state, steps to reproduce)

Well-described issues help improve the device and guide future development.

---

## Web Tool

https://sinitsinmike.github.io/Alpha1_Web_MIDI2/
