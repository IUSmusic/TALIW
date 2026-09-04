

**Thoracic Auxiliary Limb Integration - modular wearable robotics and autonomous morphing-flight research**

Project TALI investigates a non-surgical wearable platform built around a shared thoraco-pelvic chassis (`TALI-Core`) and interchangeable auxiliary modules. The project currently defines two distinct module families:

- **TALI-H** - auxiliary hand-arm robotics for manipulation, support, gripping, tool use, and quadrimanual coordination.
- **TALI-W** - an autonomous morphing flight module intended to investigate efficient human-scale glide, powered forward flight, flight-envelope protection, and automated terminal landing.

The two modules share the same core load-transfer, power, data, safety, and docking architecture but remain mechanically and functionally separate.

## Current design doctrine

TALI is a research project, not a validated human-flight system. The active architecture follows five rules:

1. **The wearer provides intent; the controller manages flight-critical detail.** In TALI-W, commands such as direction, climb/descent preference, or a landing request do not directly command individual aerodynamic surfaces or thrust units.
2. **Aerodynamics should carry most of the load in normal forward flight.** Propulsion is treated primarily as an energy-management and terminal-assist subsystem rather than as continuous jetpack-style lift.
3. **Landing is a safety-critical autonomous state transition.** After landing commitment, the system is responsible for approach management, flare, residual momentum reduction, attitude stabilization, terrain validation, final descent, and contact/load transfer.
4. **Trajectory-independent touchdown is only claimed inside a validated Recoverable Flight Envelope (RFE).** TALI-W does not assume that arbitrary speed or trajectory can be stopped in the final 5 m. The controller must begin energy removal early enough to enter the terminal landing region in a recoverable state.
5. **Passive protection is the final layer, not the primary braking system.** Air cells, crush structures, harness stroke, and other energy absorbers may reduce residual impact loads, but no gel or capsule can absorb arbitrary kinetic energy in a fixed thickness.

## System architecture

```text
                         PROJECT TALI
                              |
          +-------------------+-------------------+
          |                                       |
       TALI-H                                  TALI-W
  manipulation module                autonomous flight module
          |                                       |
          +-------------------+-------------------+
                              |
                         TALI-Core
                  thoraco-pelvic load path
                              |
                Universal Thoracic Dock (UTD)
                              |
       power | data | safety | load sensing | module ID
```

### TALI-Core

TALI-Core is the common wearable chassis. Its purpose is to transfer module loads through a posterior thoraco-pelvic structure and pelvic interface rather than terminating high loads at the shoulders, neck, ribs, or soft tissue. It also hosts shared compute, safety logic, power distribution, sensor integration, logging, and module recognition.

### Universal Thoracic Dock (UTD)

The UTD is the mechanical/electrical interface between TALI-Core and an attached module. Current work treats dock dimensions, load ratings, connector selection, and release mechanisms as engineering requirements to be derived and verified - not fixed legacy values.

### TALI-H

TALI-H remains the manipulation module. It is intended for close-range additional-arm functions such as hold, grip, brace, stabilize, support, pass, and tool interaction. The onboard controller manages detailed joint coordination, compliant contact, collision avoidance, and force limits.

### TALI-W

TALI-W is now defined as an **autonomous morphing flight system**, not merely a wing-shaped support appendage. Its research architecture combines:

- foldable/morphing lifting surfaces;
- high-lift and high-drag landing configurations;
- tail or equivalent pitch/yaw control surfaces;
- distributed sensors and flight-state estimation;
- autonomous six-degree-of-freedom control;
- efficient powered forward flight or powered-glide assistance;
- terminal-assist propulsion where required;
- an autonomous terminal landing controller; and
- passive residual-energy protection.

The biological inspiration is functional rather than anatomical. Large birds, soaring birds, raptors, alula-equipped wings, fan tails, and morphing wing geometries are treated as separate references for different aerodynamic functions.

## TALI-W landing concept

The central landing requirement is not "stop from any speed in 5 m." The current concept is:

```text
normal / high-speed flight
          |
          v
autonomous energy management
          |
          v
approach inside Recoverable Flight Envelope (RFE)
          |
          v
automatic aerodynamic flare
          |
          v
terminal momentum reduction / powered assist as required
          |
          v
Terminal Stabilization State (TSS)
          |
          |  nominal stabilization hold ~1 s (requirement remains configurable)
          v
controlled vertical descent
          |
          v
contact detection -> controlled load transfer -> landed state
```

The controller is not permitted to intentionally command touchdown until the Terminal Stabilization State is verified. If a safe terminal state cannot be reached with the remaining altitude, control authority, energy, and terrain confidence, the system must enter a predefined recovery/abort path rather than continue a nominal landing.

The final few metres are therefore a **terminal landing region**, not the entire braking distance.

## Flight-control principle

TALI-W treats the complete vehicle/person state as a controlled system. A simplified state vector is:

```text
X = [position, velocity, attitude, angular rate,
     aerodynamic configuration, propulsion state,
     remaining energy, terrain state, system health]
```

The flight computer continuously estimates whether the current state remains inside the Recoverable Flight Envelope. Human commands may request an objective, but they must not be able to force the system outside verified flight or landing constraints.

During the autonomous terminal sequence, detailed personal input is not required. A user request to abort/recover may be accepted if it leads to a safer state, but there is no manual command that bypasses the touchdown safety gate.

## Development approach

TALI-W development is deliberately staged:

```text
requirements and physics
        -> simulation
        -> component benches
        -> sub-scale unmanned flight
        -> full-scale unmanned/dummy testing
        -> tethered integrated testing
        -> independent safety review
        -> only then consider controlled human-carrying research
```

High-energy human landing trials are explicitly outside the present validation stage. Early occupied research, if ever undertaken, should retain independent conventional recovery systems wherever technically applicable.

## Repository map

- [`docs/00_VISION.md`](docs/00_VISION.md) - project scope and design doctrine.
- [`docs/01_SYSTEM_ARCHITECTURE.md`](docs/01_SYSTEM_ARCHITECTURE.md) - TALI-Core, UTD, TALI-H, and TALI-W responsibilities.
- [`docs/02_REQUIREMENTS.md`](docs/02_REQUIREMENTS.md) - active system and flight requirements.
- [`docs/03_SAFETY_PHILOSOPHY.md`](docs/03_SAFETY_PHILOSOPHY.md) - safety model and recoverability doctrine.
- [`docs/04_TEST_ROADMAP.md`](docs/04_TEST_ROADMAP.md) - staged verification path.
- [`docs/DECISIONS.md`](docs/DECISIONS.md) - architecture decisions and rationale from the current design iteration.
- [`docs/TALI-Core/`](docs/TALI-Core/) - shared chassis and Universal Thoracic Dock interface notes.
- [`docs/TALI-H/`](docs/TALI-H/) - manipulation-module overview.
- [`docs/TALI-W/`](docs/TALI-W/) - detailed TALI-W flight, control, landing, propulsion, biomimicry, and failure-mode notes.
- [`engineering/`](engineering/) - mass, power, requirements, and risk registers.
- [`simulation/`](simulation/) - reserved structure for aerodynamic, flight-dynamics, landing, and structural models.
- [`software/`](software/) - reserved structure for flight control, simulation, and telemetry code.
- [`hardware/`](hardware/) - reserved structure for CAD, electronics, and prototype records.
- [`tests/`](tests/) - verification evidence organized by test class.
- [`archive/legacy-2026-05/`](archive/legacy-2026-05/) - superseded concept material retained for traceability.

## Current project status

**Architecture / requirements stage.** No current repository value should be interpreted as a certified human-flight limit unless it is linked to recorded analysis or test evidence. Numerical parameters such as maximum mass, wing area, flight speed, landing speed, thrust, battery power, dock load rating, and terminal descent rate remain `TBD` until the corresponding model and verification record exist.

The engineering objective is to maximize safe controllable flight capability per unit added mass while maintaining recoverability, fault tolerance, and a controlled landing path.

## Master plan

The active master plan is:

- [`TALI Modular Exosuit Master Plan 2026.pdf`](TALI%20Modular%20Exosuit%20Master%20Plan%202026.pdf)
- source: [`docs/MASTER_PLAN_2026.md`](docs/MASTER_PLAN_2026.md)

The original May 2026 master plan and diagrams have been archived because their TALI-W scope and unvalidated numeric assumptions no longer match the active project direction.

## Project note

Project TALI is experimental engineering research. Human-carrying flight introduces severe aerodynamic, structural, propulsion, control, thermal, battery, and failure-tolerance hazards. Documentation in this repository describes research requirements and hypotheses, not proof of safety or regulatory approval.

Copyright (c) 2026 Project TALI / Pezhman Farhangi. All rights reserved unless otherwise stated in a specific file.
