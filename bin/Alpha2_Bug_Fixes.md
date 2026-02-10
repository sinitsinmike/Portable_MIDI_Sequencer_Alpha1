# Alpha2 — Bug Fixes & Stability Improvements

This document describes the changes introduced in **Alpha2** of the Alpha1 MIDI Sequencer project.

Alpha2 is a **stability and safety-focused release**.  
No new features were added.

---

## Alpha2 Scope (Frozen)

Alpha2 addresses the following areas only:

- Boot safety
- Load determinism
- Removal of automatic project loading on startup
- Guaranteed RAM reset on project load
- Elimination of soft-brick scenarios caused by power loss
- No new features or UI changes

---

## Summary of Fixes

### 1. Boot Safety

**Before (Alpha1):**
- Device attempted to automatically load the last-used project on startup
- If power was lost during recording or saving, flash data could become inconsistent
- Loading a corrupted project at boot could cause:
  - Black screen after boot logo
  - Device becoming unusable without reflashing firmware

**After (Alpha2):**
- Device no longer loads any project automatically on startup
- Startup always begins in a safe, neutral state
- Corrupted or incomplete projects can no longer brick the device at boot

**Why this matters:**
- Eliminates the most critical failure mode
- Ensures the device always boots reliably, regardless of previous power loss

---

### 2. Load Determinism

**Before (Alpha1):**
- Loading a project did not fully reset in-memory (RAM) state
- Loading an empty project could leave MIDI events from the previous project in RAM
- Result: unexpected playback of stale MIDI data

**After (Alpha2):**
- Loading any project **always clears all RAM state first**
- Event buffers, play indices, and playback state are reset deterministically
- Empty projects now behave as truly empty

**Why this matters:**
- Load behavior is now predictable and repeatable
- Prevents hidden state leakage between projects

---

### 3. No Auto-Load on Startup

**Before (Alpha1):**
- System implicitly depended on a "last project" mechanism
- Increased coupling between boot logic and storage integrity

**After (Alpha2):**
- No project is loaded automatically at boot
- Project loading is always an explicit user action

**Why this matters:**
- Strong separation between boot logic and project data
- Simplifies system reasoning and failure analysis

---

### 4. RAM Reset on Load

**Before (Alpha1):**
- RAM cleanup depended on project content
- Edge cases allowed partial state reuse

**After (Alpha2):**
- RAM state is cleared unconditionally before any project load
- Playback, recording, and tick counters reset to known defaults

**Why this matters:**
- Guarantees clean state transitions
- Prevents undefined behavior during playback and recording

---

## Explicitly Out of Scope (Alpha2)

The following issues are acknowledged but intentionally **not addressed** in Alpha2:

- Clear Current Project (RAM-only)
- REC-during-REC cleanup reliability
- Advanced crash recovery
- Flash journaling or transactional saves
- UX or workflow changes

These items are planned for future Alpha releases.

---

## Versioning Notes

- Project format version remains unchanged
- Existing projects created in Alpha1 remain compatible
- No migration or conversion is required

---

## Release Intent

Alpha2 is intended to:
- Stabilize the core system
- Remove catastrophic failure modes
- Provide a safe foundation for further development

Alpha2 does **not** attempt to improve usability or add features.

---

**Status:** Locked  
**Audience:** Internal / Developers / Advanced Users  
