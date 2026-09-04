# Changelog

## 0.2.0 - September 2026

Major architecture update based on the current TALI-W flight and autonomous-landing research direction.

### Changed

- Redefined TALI-W from a primarily support/bracing wing-arm into an autonomous morphing flight research module.
- Defined the wearer as a high-level intent source rather than the direct flight-control loop.
- Added Recoverable Flight Envelope (RFE) and Terminal Stabilization State (TSS) concepts.
- Reframed the "final 5 m" as a terminal landing region that must be entered in a recoverable state, not as an arbitrary high-speed stopping distance.
- Added automatic flare, terminal momentum reduction, optional short stabilization/hover, controlled descent, and touchdown gating.
- Added passive impact protection as a final safety layer rather than a substitute for velocity reduction.
- Added the design principle that aerodynamic surfaces provide most normal-flight lift while propulsion primarily manages energy and terminal control.
- Replaced single-species biomimicry with functional multi-species aerodynamic references while retaining the Kori bustard as a useful large-bird reference.
- Removed legacy unverified numeric dock and load values from the active specification.

### Added

- System architecture, requirements, safety philosophy, and staged test roadmap.
- Detailed TALI-W documents for morphing wings, flight dynamics, propulsion, autonomous control, terminal landing, passive protection, and failure modes.
- Engineering mass, power, requirement, and risk registers.
- Updated master-plan source and PDF.

### Archived

- May 2026 master plan and concept diagrams moved to `archive/legacy-2026-05/` for traceability.
