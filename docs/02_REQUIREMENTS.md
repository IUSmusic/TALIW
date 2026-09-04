# TALI Active Requirements Baseline

Version: 0.2.0  
Status: Preliminary - values marked TBD require analysis/test evidence.

This document contains the active requirement statements. The CSV matrix in `engineering/REQUIREMENT_MATRIX.csv` is the traceable register.

## Requirement language

- **SHALL** - mandatory project requirement.
- **SHOULD** - design preference subject to trade study.
- **TBD** - numerical value or method not yet established.
- **Verified** - evidence exists and is linked from the requirement register.

## A. System and modularity

**SYS-001** - TALI SHALL maintain TALI-H and TALI-W as distinct module classes on a shared TALI-Core platform.

**SYS-002** - TALI-Core SHALL provide common power, data, safety supervision, logging, module identification, and human-interface services.

**SYS-003** - Active performance limits SHALL be configuration-controlled and SHALL NOT rely on superseded legacy diagrams.

**SYS-004** - Any numerical limit presented as a system specification SHALL have an identified analysis or verification method.

## B. TALI-Core / UTD

**CORE-001** - TALI-Core SHALL route operational module loads through a designed posterior thoraco-pelvic load path rather than intentionally terminating high loads at the neck, clavicle, axilla, or unsupported ribs.

**CORE-002** - TALI-Core SHALL monitor human-interface conditions needed to identify loss of fit, abnormal load transfer, or unsafe attachment state where practicable.

**UTD-001** - The UTD SHALL provide positive mechanical alignment and locking.

**UTD-002** - The UTD SHALL provide independent indication of lock state before force- or flight-capable operation is enabled.

**UTD-003** - The UTD SHALL identify the attached module and load the correct configuration before enabling active authority.

**UTD-004** - UTD structural ratings SHALL be derived from flight/manoeuvre/landing load cases with defined safety factors; current values are TBD.

## C. TALI-W flight architecture

**W-FLT-001** - TALI-W SHALL be treated as an autonomous morphing aircraft module rather than a manually coordinated set of wing joints.

**W-FLT-002** - TALI-W SHALL estimate six-degree-of-freedom vehicle state and relevant aerodynamic, energy, terrain, and health states at rates sufficient for control.

**W-FLT-003** - Normal forward flight SHOULD use aerodynamic lift to support the majority of system weight whenever the flight condition permits.

**W-FLT-004** - Continuous powered hover SHALL NOT be assumed as the primary cruise regime.

**W-FLT-005** - The flight controller SHALL constrain commands to the validated flight envelope.

**W-FLT-006** - The controller SHALL maintain or recover toward the Recoverable Flight Envelope (RFE) when an operator request conflicts with recoverability.

**W-FLT-007** - Morphing wing, tail, high-lift, and drag devices SHALL be controlled according to measured/estimated flight state rather than fixed timing alone.

## D. Recoverable Flight Envelope

**W-RFE-001** - TALI-W SHALL define an RFE as the set of validated states from which a safe state is reachable under specified disturbance and failure assumptions.

**W-RFE-002** - The RFE model SHALL include, at minimum, velocity, altitude/position, attitude, angular rate, available control authority, remaining energy, and system-health state.

**W-RFE-003** - Terrain suitability and environmental uncertainty SHALL be included wherever they materially affect the ability to land safely.

**W-RFE-004** - The controller SHALL detect impending exit from the RFE early enough to take an available recovery action.

**W-RFE-005** - "Trajectory-independent landing" SHALL only be claimed for approach states demonstrated to converge to the required terminal state inside the validated RFE.

## E. Autonomous terminal landing

**W-LND-001** - Once `LAND_COMMIT` occurs, detailed terminal landing control SHALL be autonomous and SHALL NOT require continuous personal input.

**W-LND-002** - The landing controller SHALL manage approach energy, flare, residual momentum reduction, attitude stabilization, terrain validation, terminal descent, contact detection, and load transfer.

**W-LND-003** - The final few metres SHALL be treated as a terminal landing region entered only after preceding energy management has established a recoverable state.

**W-LND-004** - TALI-W SHALL NOT assume that arbitrary high-speed flight can be stopped safely inside 5 m.

**W-LND-005** - TALI-W SHALL define a Terminal Stabilization State (TSS) containing bounded translational velocity, vertical rate, angular rate, attitude, terrain confidence, remaining energy, and system-health criteria.

**W-LND-006** - The controller SHALL inhibit intentional final descent/touchdown while TSS is false.

**W-LND-007** - If TSS cannot be reached before the applicable decision boundary, the controller SHALL transition to a defined recovery/abort state rather than continue the nominal landing sequence.

**W-LND-008** - The baseline landing concept SHOULD include a short stabilization hold after TSS and before descent. The current research nominal is approximately 1 second; the final duration is TBD and SHALL be validated.

**W-LND-009** - The final descent rate and touchdown state limits are TBD and SHALL be established from human tolerance, landing-structure capability, and system-control evidence.

**W-LND-010** - Operator input SHALL NOT provide a bypass that commands touchdown when the touchdown safety gate is false.

## F. Propulsion and energy

**W-PWR-001** - Propulsion architecture SHALL be sized against the complete mission and emergency load cases, including terminal control authority, not only steady cruise.

**W-PWR-002** - Propulsion selection SHALL consider thrust-to-mass, propulsive efficiency, disk/loading or equivalent flow area, deployment volume, thermal limits, redundancy, failure effects, and control bandwidth.

**W-PWR-003** - The project SHOULD prioritize aerodynamic energy removal before using powered terminal arrest when that reduces system mass and power without reducing recoverability.

**W-PWR-004** - A short stabilization/hover duration SHALL NOT be used as evidence that a small energy store is sufficient unless the kinetic energy of the preceding arrest manoeuvre, peak power, losses, reserves, and failure cases are also included.

**W-PWR-005** - Remaining energy SHALL be part of the RFE and landing-commit decision.

## G. Passive protection

**W-PAS-001** - Passive impact protection SHALL be designed for a bounded residual impact envelope.

**W-PAS-002** - Passive protection SHALL NOT be represented as capable of protecting against arbitrary mass or impact speed.

**W-PAS-003** - Candidate passive systems MAY combine controlled-vent air cells, crushable structures, compliant landing members, harness stroke, and load-spreading interfaces.

**W-PAS-004** - Passive protection performance SHALL be verified using instrumented surrogate mass/inertia before any human exposure to equivalent impact energy.

## H. Control and sensing

**W-CTL-001** - Safety-critical state estimation SHALL use redundancy/diversity appropriate to the identified hazards.

**W-CTL-002** - The controller SHALL detect and manage sensor disagreement rather than blindly averaging incompatible measurements.

**W-CTL-003** - Flight-critical control SHALL remain local to the vehicle and SHALL NOT depend on an external network connection.

**W-CTL-004** - Safety-critical software and parameters SHALL be configuration-controlled and logged.

**W-CTL-005** - The system SHALL record sufficient telemetry to reconstruct flight-mode transitions, safety-gate decisions, and anomalies.

## I. Failure tolerance

**W-SAF-001** - A formal Functional Hazard Assessment SHALL precede occupied free-flight testing.

**W-SAF-002** - A Preliminary System Safety Assessment SHALL allocate mitigations for identified catastrophic and hazardous failure conditions before occupied free-flight testing.

**W-SAF-003** - The target architecture SHALL prevent any identified credible single failure from directly commanding an uncontrolled touchdown where a practicable independent mitigation can be designed.

**W-SAF-004** - Loss of an individual sensor, actuator, propulsor, compute lane, or power path SHALL be analysed for flight and landing consequences.

**W-SAF-005** - Research prototypes SHALL include an independent test termination/recovery strategy appropriate to their scale, energy, and occupancy.

## J. Verification progression

**W-VER-001** - Human-carrying free flight SHALL NOT be used to discover basic aerodynamic stability, actuator authority, or landing-state-machine defects that can be tested unmanned.

**W-VER-002** - TALI-W SHALL progress through simulation, component bench, sub-scale unmanned, full-scale unmanned/surrogate, tethered, independent review, and only then any justified occupied free-flight stage.

**W-VER-003** - Each envelope expansion SHALL identify the evidence supporting the new limit.

**W-VER-004** - Test data SHALL be traceable to hardware configuration, mass properties, software revision, environmental conditions, and requirement IDs.
