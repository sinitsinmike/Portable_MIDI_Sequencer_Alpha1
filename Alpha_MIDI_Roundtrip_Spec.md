Alpha Sequencer – MIDI Roundtrip Architecture (Controlled Format)

Overview
This document defines the architecture for controlled bidirectional editing between Alpha Hardware Sequencer (BIN format), Alpha Web Tool, and DAW (via MIDI Format 1). The system supports Alpha-exported MIDI only for safe re-import.

Goals
	1.	Safe backup: Device → BIN → PC
	2.	Restore: BIN → Device
	3.	MIDI export for DAW editing
	4.	Controlled MIDI re-import
	5.	Future support for loop and tempo roundtrip

Supported MIDI Format
Standard MIDI File (SMF)
Format 1
Fixed PPQ = 96
Track 0 = Tempo Track (Meta Only)
Track 1..N = Sequencer Tracks
No external MIDI parsing support

Import supports only Alpha-generated MIDI files.
This guarantees stable structure, no track shifting, no broken channel mapping, and no unknown data parsing.

Tempo Track (Track 0)
Contains:
	1.	Tempo Meta Event (FF 51 03 tt tt tt)
	2.	Optional future Alpha Custom Meta (FF 7F length “ALPHA_LOOP start end”)
	3.	End Of Track (FF 2F 00)

Tempo track is separate and does NOT overwrite musical tracks.

Musical Tracks (1..N)
Each track contains:
	1.	Track Name Meta Event (FF 03 “Track X”)
	2.	MIDI note events (Note On / Note Off)
	3.	End Of Track (FF 2F 00)

Empty tracks are preserved.
No automatic deletion.
No track index shifting.

This guarantees safe re-import and channel stability.

Loop Strategy (Future Safe Implementation)
LoopStart and LoopEnd will be stored using Sequencer Specific Meta (FF 7F).
Vendor identifier: “ALPHA”.
Payload contains loopStartTick and loopEndTick.

Marker meta is not reliable for roundtrip logic because it is visual-only, DAWs may move it, and it does not define behavior. Custom meta is invisible to DAW editing but preserved in the file.

Tick Conversion
Engine PPQ = 96
MIDI PPQ = 96

Scale factor currently equals 1, so engineTick equals midiTick.
If PPQ changes in future, engineTick = midiTick multiplied by ENGINE_PPQ divided by MIDI_PPQ.

Ticks are mandatory. Without ticks, timing collapses.

Safety Guarantees
No track deletion
No channel shifting
No unknown meta parsing
No DAW marker dependency
Tempo track isolated
Roundtrip stable

Current Status
Multi-track export implemented
Tempo meta event implemented
Track names implemented
Stable timing
Safe structure

Next Priority
BIN upload to device
Full project restore from PC

Future Roadmap
Phase 2:
BIN → Device upload
Full project restore

Phase 3:
Controlled MIDI re-import
Loop meta roundtrip
Tempo roundtrip
External editing workflow

Product Vision
Alpha becomes a Hardware Sequencer plus DAW External Editor plus Safe Project Roundtrip Ecosystem without full MIDI parser complexity.

Loop Marker Status
Current loop marker in tempo track is harmless.
It does not affect sound.
DAWs ignore it safely.
It does not break re-export.
It can remain until custom loop meta is implemented.

Strategic Direction
First: Implement BIN upload back to device.
That enables Device → BIN → PC → Device backup restore workflow.

Second: MIDI → DAW edit → MIDI → BIN → Device roundtrip.

That creates a controlled, professional external editing ecosystem.