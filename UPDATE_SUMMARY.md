# TALI 0.2.0 Update Summary

This revision aligns the repository with the September 2026 design discussion.

## Active architectural changes

- TALI-W is now an autonomous morphing-flight research module.
- TALI-H remains the separate manipulation module.
- TALI-Core and the UTD remain shared infrastructure, but legacy numeric UTD ratings are no longer active specifications.
- Human flight commands are intent-level; flight stabilization and terminal landing are machine-controlled.
- The Recoverable Flight Envelope (RFE) is the boundary for any claim of autonomous safe recovery/landing.
- The Terminal Stabilization State (TSS) is a mandatory gate before final controlled descent.
- The approximately one-second pre-touch stabilization concept is retained as a research nominal, not a frozen value.
- The final 5 m is defined as a terminal landing region, not a universal high-speed stopping distance.
- Aerodynamic braking/lift should remove as much energy as practical before terminal propulsion is used.
- Propulsion topology is deliberately open pending an installed-mass, power, control-authority, and failure-tolerance trade study.
- Passive gels/capsules/airbags/crush systems are residual-energy protection only.
- Bird inspiration is now multi-species and functional; Kori bustard is retained as one large-bird reference.
- Development proceeds through simulation and unmanned/surrogate testing before any equivalent human exposure.

## Files added

- project vision and architecture;
- formal requirements baseline;
- safety philosophy;
- verification roadmap;
- TALI-Core and UTD notes;
- TALI-H overview;
- TALI-W overview, flight dynamics, morphing wing, propulsion, autonomous control, terminal landing, passive protection, and failure modes;
- biological flight research references;
- mass, power, requirement, and risk registers;
- architecture decision record;
- revision changelog and version file;
- revised master-plan source and PDF.

## Files archived

The May 2026 PDF and original concept diagrams are in `archive/legacy-2026-05/`. They remain available for historical traceability but are not current specifications.
