## Interfaces

One of the biggest causes of project pain is unclear interfaces.

Document things like:

Pixhawk ↔ Companion Computer
Companion ↔ Camera
Ground Station ↔ Telemetry
Companion ↔ Flight Controller (MAVLink)
Payload ↔ Power Bus

This pays dividends later when you're integrating hardware and software.