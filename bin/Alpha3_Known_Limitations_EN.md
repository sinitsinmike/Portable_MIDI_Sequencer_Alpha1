# Known Limitations (Alpha3)

-   Maximum project size is limited to one flash sector (4096 bytes)
-   Maximum MIDI events per project ≈ 500
-   Storage uses fixed-size project format (VERSION = 2)
-   Dynamic multi-sector storage is not yet implemented

------------------------------------------------------------------------

# Design Limitation

Current project storage uses a fixed flash sector per project.

This provides:

-   Structural simplicity
-   Deterministic write behavior
-   Predictable flash operations

However, this limits the maximum number of events per project.

Future versions are planned to introduce dynamic sector allocation.
