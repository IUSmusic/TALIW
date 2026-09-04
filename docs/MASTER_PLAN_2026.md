---
title: "TALI Modular Thoracic Auxiliary Limb Exosuit"
subtitle: "Official Design Master Plan - Architecture Revision 0.2"
author: "Project TALI / Pezhman Farhangi"
date: "September 2026"
geometry: margin=1in
toc: true
fontsize: 10pt
---

# Document status

This document supersedes the active design direction in the May 2026 TALI master plan while preserving that earlier document in `archive/legacy-2026-05/` for traceability.

Revision 0.2 changes TALI-W from a primarily ground-support/bracing wing-arm into an autonomous morphing-flight research module. It also introduces formal recoverability and autonomous-landing concepts.

This is a research architecture and requirements document. It is not evidence that the system is safe for human flight, is not regulatory approval, and does not assign validated performance numbers where evidence does not yet exist.

# 1. Project definition

Project TALI is a modular, non-surgical wearable robotics programme built around an external thoraco-pelvic platform. The project translates the original thoracic auxiliary-limb concept into removable engineered hardware rather than implanted biological structures.

The project contains four primary architectural elements:

1. **TALI-Core** - shared thoraco-pelvic structural, electrical, computational, sensing, and safety platform.
2. **Universal Thoracic Dock (UTD)** - controlled module interface between TALI-Core and mission modules.
3. **TALI-H** - additional hand-arm manipulation module.
4. **TALI-W** - autonomous morphing-flight module.

TALI-H and TALI-W use common infrastructure but remain separate mechanical systems with different requirements, hazards, and verification paths.

# 2. Design doctrine

## 2.1 Intent-level human control

The wearer provides high-level intent. The machine coordinates detailed actuation.

For TALI-H, intent may include hold, grip, release, brace, stabilize, or pass an object.

For TALI-W, intent may include heading, turn, climb, descend, speed preference, land, or recover. The human is not expected to manually coordinate wing segments, tail surfaces, propulsors, or flare timing.

## 2.2 Recoverability is a primary flight constraint

TALI-W shall operate inside a validated Recoverable Flight Envelope (RFE). The RFE represents states from which the system has a verified path to an acceptable safe state under the applicable disturbance, system-health, and energy assumptions.

The controller shall prioritize preserving or regaining recoverability over fulfilling a conflicting operator request.

## 2.3 Aerodynamics before continuous powered lift

The mass-efficient design hypothesis is that normal forward flight should use aerodynamic lifting surfaces to support most of the human-system weight. Propulsion should primarily replace energy lost to drag, provide climb capability, maintain control margins, and supply terminal landing authority.

Continuous powered hover is not the primary cruise objective.

## 2.4 Landing is an autonomous state conversion

The project objective is not to stop any incoming trajectory in the final 5 m. Instead, the controller shall begin energy management early enough that the final terminal region is entered in a recoverable state.

Different approach states inside the validated RFE should converge to a bounded Terminal Stabilization State (TSS), after which controlled descent and touchdown can occur.

## 2.5 Passive protection is residual protection

Gel, foam, inflatable cells, crush structures, or a capsule cannot remove arbitrary kinetic energy over a fixed thickness. These systems remain valuable when designed for the bounded residual impact state left after active aerodynamic and powered control.

# 3. System-level architecture

```text
Human wearer
     |
     v
TALI-Core
  |-- human interface
  |-- power/data distribution
  |-- safety supervisor
  |-- logging and configuration
  |-- thoraco-pelvic load path
     |
Universal Thoracic Dock
     |
     +---------------------+
     |                     |
   TALI-H                TALI-W
 manipulation       autonomous flight
```

The shared core provides common infrastructure. Module-specific safety logic and computers may exist where required by the hazard analysis.

# 4. TALI-Core

TALI-Core is a wearable chassis spanning the posterior thorax and pelvis. Its functions are:

- transfer module loads through designed structural paths;
- distribute human-interface pressure;
- retain and align the module interface;
- provide power and data services;
- host or supervise safety-critical electronics;
- provide system health and emergency state functions;
- maintain configuration and wearer calibration data;
- log data for engineering traceability.

Flight loads differ substantially from auxiliary-arm loads. Therefore the TALI-W structural path must be re-derived from aerodynamic, manoeuvre, gust, propulsion, landing, and failure loads. Legacy dock ratings are superseded until substantiated.

# 5. Universal Thoracic Dock

The UTD shall provide a controlled structural/electrical interface. Exact geometry remains open.

Required functions include:

- keyed mechanical alignment;
- positive locking;
- independent lock-state sensing;
- power connection;
- deterministic data connection;
- module identification;
- structural load/strain measurement where useful;
- safety interlock;
- controlled service/emergency release;
- optional fluid services only if justified by a module architecture.

A module shall not receive flight- or high-force authority until identity and lock state are verified.

# 6. TALI-H manipulation module

TALI-H remains the close-range additional-arm system. The module should use compact arms with low distal mass, modular end effectors, compliant force control, collision monitoring, and intent-level operation.

Candidate end-effector classes include:

- adaptive robotic hands;
- parallel or angular grippers;
- clamps;
- hooks;
- tool interfaces;
- stabilization pads.

TALI-H has a separate verification path from TALI-W and does not inherit flight requirements.

# 7. TALI-W autonomous morphing-flight module

## 7.1 Definition

TALI-W is a wearable, deployable, morphing aircraft module intended to investigate:

- controllable glide;
- powered forward flight;
- aerodynamic energy management;
- autonomous flight-envelope protection;
- automatic flare;
- powered terminal assistance where required;
- autonomous terminal stabilization;
- controlled touchdown;
- passive residual-energy protection.

## 7.2 Functional biomimicry

No single bird is treated as a complete design template.

The Kori bustard remains a useful reference for large-body biological flight. Other biological functions are considered separately:

- soaring birds for efficient glide;
- raptors/perching birds for flare and braking;
- alula-equipped wings for high-angle-of-attack flow control;
- fan tails for low-speed stability and control;
- general avian wing morphing for stability/agility changes.

Biological inspiration generates hypotheses; it does not set human-scale dimensions.

## 7.3 Morphing aerodynamic system

Candidate controlled geometry includes:

- deployable span;
- variable sweep;
- variable camber;
- wing twist;
- segmented trailing edges;
- leading-edge high-lift devices;
- alula-like devices;
- spoilers/drag surfaces;
- deployable tail area.

The preferred final mechanism is the minimum set that provides sufficient efficiency, control authority, flare capability, and fault tolerance at acceptable mass.

## 7.4 Structural principles

TALI-W should pursue:

- high-specific-stiffness primary structure;
- mechanically lockable load-bearing joints;
- low distal mass;
- proximal placement of heavy actuation where feasible;
- tensioned/inflatable/lightweight secondary aerodynamic surfaces where advantageous;
- explicit analysis of deployment dynamics and asymmetric failure.

Candidate material classes include carbon-fibre composites, aluminium/titanium fittings, reinforced fabrics/films, and lightweight cellular or inflatable structures. Materials are not baselined until verified against the required load and environmental cases.

# 8. Flight physics baseline

## 8.1 Lift and drag

First-order aerodynamic forces are:

$$
L = \frac{1}{2}\rho V^2 S C_L
$$

$$
D = \frac{1}{2}\rho V^2 S C_D
$$

These equations establish two important constraints:

1. useful aerodynamic force falls rapidly as airspeed approaches zero;
2. larger lifting area can reduce characteristic flight speed but creates structural, deployment, and mass penalties.

A fixed wing cannot provide a stationary one-second hover in still air without another force-producing mechanism.

## 8.2 Kinetic energy

$$
E_k = \frac{1}{2}mv^2
$$

Impact or arrest energy grows with the square of speed.

For constant deceleration:

$$
a = \frac{v_i^2-v_f^2}{2d}
$$

Therefore a 5 m terminal region cannot safely remove arbitrary high-speed momentum. TALI-W must reduce energy earlier according to the current state.

# 9. Flight-control architecture

TALI-W requires autonomous six-degree-of-freedom control.

A simplified state is:

$$
X = [p, v, q, \omega, c_{wing}, u_{prop}, E, terrain, health]
$$

where position, velocity, attitude, angular rate, wing configuration, propulsion state, energy, terrain, and system health are all relevant to safe control.

The control stack is:

```text
wearer intent
   -> mission/mode manager
   -> guidance
   -> RFE / safety constraint supervisor
   -> attitude/rate/trajectory control
   -> control allocation
   -> wing + tail + propulsion + landing mechanisms
```

Flight-critical control shall be local to the system and shall not depend on internet/cloud availability.

# 10. Recoverable Flight Envelope

The RFE shall be defined quantitatively after simulation and test data exist.

At minimum it should include:

- velocity vector;
- altitude and terrain-relative position;
- attitude and angular rates;
- current wing configuration;
- available aerodynamic control authority;
- available propulsion/control authority;
- remaining energy and thermal margins;
- structural/load margins;
- sensor confidence;
- system-health/fault state;
- wind/gust uncertainty where applicable.

The controller must detect decreasing recoverability before the remaining options disappear.

# 11. Autonomous terminal landing

## 11.1 Landing state machine

```text
FLIGHT
  -> APPROACH_ENERGY_MANAGEMENT
  -> LAND_COMMIT
  -> AUTOMATIC_FLARE
  -> TERMINAL_ARREST
  -> TERMINAL_STABILIZATION_STATE
  -> CONTROLLED_DESCENT
  -> CONTACT_DETECTION
  -> CONTROLLED_LOAD_TRANSFER
  -> LANDED_SAFE
```

Any safety-critical gate failure routes to a recovery/abort path where a physically valid recovery remains.

## 11.2 Terminal Stabilization State

TSS is the state that separates high-energy flight from final descent.

Candidate criteria are bounded:

- horizontal speed;
- vertical speed;
- attitude;
- angular rates;
- terrain-relative position;
- landing surface confidence;
- control reserve;
- energy reserve;
- critical system health.

All numerical limits are currently TBD.

## 11.3 Stabilization hold

The current research concept includes approximately one second of stabilization after TSS and before final contact. This is a nominal research value, not a frozen requirement.

The value of the hold is architectural: it requires the system to establish a distinct controlled terminal state rather than allowing touchdown to be the end of an uncontrolled high-speed trajectory.

## 11.4 Touchdown gate

Intentional final descent is inhibited unless TSS is true and the required terrain, energy, and system-health margins are present.

The wearer cannot bypass this gate. A recovery request may be accepted if it produces a safer trajectory.

# 12. Propulsion and energy

## 12.1 Propulsion role

Propulsion topology remains a trade study.

Large-area foldable propulsors are a candidate because low disk loading can improve hover/low-speed induced efficiency, but packaging, strike hazard, structural reaction loads, deployment, and single-unit failure must be solved.

Ducted fans, turbines/jets, flapping systems, or other methods remain comparison candidates until the installed mass and safety trade is complete.

## 12.2 Ideal hover relationship

A first-order momentum-theory induced-power expression is:

$$
P_i \approx \frac{W^{3/2}}{\sqrt{2\rho A}}
$$

where `A` is total effective disk area.

This is only an ideal term. Real installed power is higher.

## 12.3 One-second hover does not define battery size

The energy required for a one-second hold may be small compared with sustained hover. The complete landing energy budget must also include:

- kinetic energy removed during terminal arrest;
- propulsive losses;
- peak power capability;
- thermal constraints;
- attitude/control impulse;
- go-around/recovery reserve;
- degraded-system cases.

Thus battery/fuel mass cannot be inferred from hover duration alone.

# 13. Passive landing protection

Passive protection is designed only after the active landing system defines the residual impact envelope.

Candidate layers include:

- compliant first contact;
- long-stroke landing members;
- controlled-vent air cells;
- sacrificial crush structures;
- internal harness stroke;
- broad load distribution through the torso/pelvis support.

An inflatable or gel-filled capsule may help at bounded residual speeds, but it cannot safely absorb arbitrary kinetic energy in a fixed wearable thickness.

A near-ground air-cushion/skirt concept may be investigated as supplemental terminal support. It requires separate validation for surface leakage, roughness, lateral motion, crosswind, debris, and transition from free-air control.

# 14. Sensors and avionics

Candidate flight-relevant sensing includes:

- redundant IMUs;
- airspeed/pressure sensing;
- GNSS where useful;
- radar/lidar range and altitude;
- optical terrain-relative navigation;
- wing/actuator position;
- structural load/strain;
- propulsion state;
- energy state;
- UTD lock/load state.

Redundancy must not be treated as simple duplication. Common-mode failure, shared power, shared software, environmental vulnerability, and correlated error require explicit analysis.

# 15. Failure tolerance and safety assessment

Before occupied free flight, TALI-W requires formal safety analysis including an FHA and PSSA, with FMEA/FMECA, fault trees, common-cause analysis, and installation/energy hazard analyses as appropriate.

The target architecture is that no identified credible single failure directly commands an uncontrolled touchdown when a practicable independent mitigation exists.

Priority failure cases include:

- erroneous inertial or altitude sensing;
- terrain-classification error;
- wing actuator jam;
- asymmetric deployment;
- propulsor loss or stuck command;
- power-bus loss;
- flight-computer failure;
- software state-transition error;
- battery thermal event;
- structural overload/failure;
- UTD unlock/false-lock indication;
- unexpectedly severe gusts;
- insufficient energy reserve;
- human incapacitation.

# 16. Development assurance references

TALI is not asserting certification to any of the following standards. They are process references for future safety-critical development.

As of this revision:

- SAE ARP4754B (revised December 2023) provides current guidelines for civil aircraft and system development.
- SAE ARP4761A (revised December 2023) provides current civil-aircraft/system safety-assessment guidance.
- SAE AIR6218A (revised May 2026) supplements ARP4754B planning for integrated systems.
- RTCA DO-178C remains the current core software assurance document referenced by FAA guidance for airborne software.
- RTCA DO-254 addresses airborne electronic hardware assurance.
- EASA's small-category VCA / SC-VTOL materials provide useful current examples of landing, controllability, and continued-safe-flight-and-landing thinking for VTOL-capable aircraft.

Applicability to TALI depends on future vehicle classification and authority determination.

# 17. Verification roadmap

## Phase 0 - physics, requirements, and simulation

Build the mass, aerodynamic, propulsion, structural, RFE, and six-degree-of-freedom landing models.

## Phase 1 - component bench testing

Measure actual wing joint, actuator, sensor, propulsion, energy, structural, and passive-protection performance.

## Phase 2 - sub-scale unmanned flight

Demonstrate morphing aerodynamics, autonomous glide, stability, flare, and low-energy recovery.

## Phase 3 - sub-scale terminal landing

Approach from varied conditions inside a defined RFE and demonstrate convergence to a common bounded TSS. Demonstrate touchdown inhibition and recovery when TSS is intentionally unreachable.

## Phase 4 - full-scale unmanned mass/inertia surrogate

Validate full-scale structural loads, deployment, propulsion, energy, landing, and passive-protection behavior without exposing a person.

## Phase 5 - tethered integrated research

Validate wearable fit, control interaction, low-energy stabilization, and autonomy without free-flight exposure.

## Phase 6 - independent review

Review structural substantiation, software/control assurance, hazards, recovery, environmental limits, and accumulated evidence.

## Phase 7 - occupied research only if justified

Human-carrying flight must not be used as the first test of basic stability or landing logic. Envelope expansion should be incremental and supported by evidence.

# 18. Engineering configuration and evidence

Every hardware test/flight shall record:

- article ID;
- complete installed mass and centre of gravity;
- wing geometry/configuration;
- propulsor/energy configuration;
- sensor set;
- software commit and parameter set;
- RFE version;
- test limits;
- environment;
- requirement IDs;
- raw-data location;
- anomalies and disposition.

The repository engineering registers are:

- `engineering/MASS_BUDGET.csv`
- `engineering/POWER_BUDGET.csv`
- `engineering/REQUIREMENT_MATRIX.csv`
- `engineering/RISK_REGISTER.csv`

# 19. Current milestone plan

**M0 - Architecture revision freeze:** Current documents and requirement IDs reviewed.

**M1 - Executable 6-DOF model:** Glide, powered flight, flare, TSS, touchdown gate, and recovery states implemented in simulation.

**M2 - Aerodynamic trade baseline:** Candidate wing/tail/morphing geometry has estimated polars and uncertainty ranges.

**M3 - Propulsion trade baseline:** Candidate terminal propulsion systems compared by installed mass, control authority, power, energy, and hazards.

**M4 - Sub-scale morphing demonstrator:** Autonomous stable flight and configuration changes demonstrated unmanned.

**M5 - Sub-scale terminal landing demonstrator:** Multiple approach states converge to TSS; unsafe descent is inhibited.

**M6 - Full-scale structural and mass-surrogate article:** Representative loads and terminal manoeuvres demonstrated without a human occupant.

**M7 - Safety architecture baseline:** FHA/PSSA and independent recovery strategy support the next test phase.

**M8 - Tethered human-interface demonstrator:** Low-energy integration validates fit, autonomy, and load transfer.

Any later occupied free-flight milestone requires a separate test plan and independent approval process.

# 20. Immediate work packages

1. Build the six-degree-of-freedom TALI-W simulation.
2. Establish an initial mass range and candidate wing area sweep rather than choosing one wing size by intuition.
3. Generate aerodynamic polars for fast, cruise, high-lift, and flare configurations.
4. Define a first conservative RFE and terminal-state model.
5. Implement the landing state machine in simulation.
6. Perform propulsion architecture trade studies using installed mass and terminal arrest requirements.
7. Build and test morphing wing mechanisms on the bench.
8. Create the first sub-scale unmanned demonstrator.
9. Start formal hazard analysis before any high-energy full-scale testing.

# References

- SAE International. ARP4754B, *Guidelines for Development of Civil Aircraft and Systems*, revised 20 December 2023. https://saemobilus.sae.org/standards/arp4754b-guidelines-development-civil-aircraft-systems
- SAE International. ARP4761A, *Guidelines for Conducting the Safety Assessment Process on Civil Aircraft, Systems, and Equipment*, revised 20 December 2023. https://saemobilus.sae.org/standards/arp4761a-guidelines-conducting-safety-assessment-process-civil-aircraft-systems-equipment
- SAE International. AIR6218A, *Constructing a Development Assurance Plan for Integrated Systems*, revised 15 May 2026. https://saemobilus.sae.org/standards/air6218a-constructing-development-assurance-plan-integrated-systems
- RTCA. DO-178C, *Software Considerations in Airborne Systems and Equipment Certification*. https://www.rtca.org/do-178/
- EASA. *Special Condition for VTOL and Means of Compliance*. https://www.easa.europa.eu/en/document-library/product-certification-consultations/special-condition-vtol
- EASA. *Easy Access Rules for small category VCA*. https://www.easa.europa.eu/en/document-library/easy-access-rules/easy-access-rules-small-category-vca
- Harvey, C., Baliga, V. B., Wong, J. C. M., et al. (2022). *Birds can transition between stable and unstable states via wing morphing*. Nature 603, 648-653. https://doi.org/10.1038/s41586-022-04477-8
- Lee, S., Kim, J., Park, H., et al. (2015). *The Function of the Alula in Avian Flight*. Scientific Reports 5, 9914. https://doi.org/10.1038/srep09914
- Smithsonian's National Zoo and Conservation Biology Institute. *Kori bustard*. https://nationalzoo.si.edu/animals/kori-bustard
