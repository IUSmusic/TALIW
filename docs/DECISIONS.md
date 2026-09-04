# TALI Architecture Decision Record

## ADR-001 - TALI-W is a flight module

**Decision:** TALI-W is defined as an autonomous morphing-flight module. Ground bracing/support may exist as incidental capability but is no longer its primary identity.

**Reason:** The active project objective is controllable glide/powered flight and automatic safe terminal landing.

## ADR-002 - Human input is intent-level

**Decision:** The wearer does not manually coordinate flight-critical surfaces during normal control or terminal landing.

**Reason:** Human reaction and coordination cannot be the primary safety mechanism for a multi-actuator morphing aircraft, particularly during the last seconds of flight.

## ADR-003 - Recoverable Flight Envelope

**Decision:** Claims about safe autonomous landing are limited to a validated RFE.

**Reason:** Speed, altitude, trajectory, control authority, remaining energy, weather, terrain, and failures determine whether a safe terminal state is physically reachable.

## ADR-004 - Final 5 m is a terminal region

**Decision:** The final 5 m is not specified as the full stopping distance from arbitrary high-speed flight.

**Reason:** Kinetic energy and stopping-distance physics make that requirement incompatible with bounded human acceleration at high speed. Braking/energy management must begin earlier when required.

## ADR-005 - Terminal Stabilization State

**Decision:** Final descent is gated by a TSS. The current concept includes an approximately one-second stabilization hold before controlled contact; final duration and bounds are TBD.

**Reason:** This separates the high-energy flight trajectory from the touchdown state and allows varied admissible approaches to converge to one bounded landing condition.

## ADR-006 - Aerodynamics carry; propulsion manages energy

**Decision:** TALI-W should use aerodynamic lift for most normal forward-flight support and avoid continuous powered hover as its primary cruise mode.

**Reason:** This is the leading architecture for reducing installed propulsion/energy mass while still enabling sustained flight and terminal control.

## ADR-007 - Propulsion topology remains open

**Decision:** Large-area foldable electric propulsors are a strong terminal-assist candidate, but no rotor/fan/jet/flapping architecture is frozen.

**Reason:** Installed mass, terminal thrust, peak power, deployment, failure tolerance, thermal hazards, and aerodynamic interaction must be evaluated together.

## ADR-008 - Passive protection is residual protection

**Decision:** Gel, airbags, crush structures, capsules, and cushions may protect against a bounded residual impact envelope only.

**Reason:** A passive wearable device cannot absorb arbitrary kinetic energy within fixed deformation distance.

## ADR-009 - Biomimicry is functional and multi-species

**Decision:** Kori bustard remains one reference, but different biological systems are used for different functions: large-body flight, soaring efficiency, flare/braking, alula flow control, tail control, and morphing.

**Reason:** No single bird maps directly to a human-scale wearable aircraft.

## ADR-010 - Human testing follows unmanned verification

**Decision:** Basic aerodynamic, control, landing, and fault behavior must be discovered and validated with simulation and unmanned/surrogate articles before equivalent human exposure.

**Reason:** Human-carrying flight is a high-consequence test environment and should not be the first mechanism for discovering avoidable system defects.
