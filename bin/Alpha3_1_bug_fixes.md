[Alpha3] – Web Integration Milestone

Added
	•	WebSerial browser interface
	•	Raw project DUMP <n> command
	•	Raw project UPLOAD <n> command
	•	Direct BIN export/import via browser
	•	MIDI export (Type 1, multi-track)
	•	MIDI import support
	•	Automatic BPM detection from MIDI tempo meta event
	•	PPQ scaling (external PPQ → internal 96 PPQ engine)
	•	Tempo track generation in exported MIDI
	•	Track Name meta events
	•	Upload confirmation protocol:
	•	READY
	•	WRITING
	•	DONE
	•	Upload timeout protection in Web tool
	•	Project backup workflow (device ↔ browser)
	•	Full DAW round-trip editing support

⸻

Changed
	•	Flash operations fully dual-core safe
	•	core1 pause before erase/program
	•	interrupt save/restore enforced
	•	System project (Project 0) separated from user projects
	•	Header validation added (magic + version checks)
	•	BPM validation with safe fallback (30–300 range)
	•	Web tool upload logic waits for explicit device confirmation
	•	Improved Serial protocol stability

⸻

Fixed
	•	Flash corruption caused by active core1 during erase/program
	•	Unreliable upload completion detection
	•	Invalid BPM (0) when importing MIDI without tempo handling
	•	PPQ mismatch causing timing distortion
	•	Missing upload success feedback in Web UI

⸻

Architecture
	•	Raw sector-level project access
	•	Deterministic flash layout
	•	Stable 4096-byte project format (VERSION = 2)
	•	Multi-track MIDI export structure
	•	Internal engine remains fixed 96 PPQ resolution

⸻

Workflow Enabled

Device → Web Tool → MIDI → DAW → MIDI → Device

Full external editing loop now supported.

⸻

Notes
	•	Project storage still uses fixed 4096-byte sectors
	•	Dynamic multi-sector project storage planned for future versions
	•	Only MIDI format 1 officially supported