# TALI Vision and Design Doctrine

Version: 0.2.0  
Status: Active research definition  
Date: September 2026

## 1. Purpose

Project TALI investigates a modular, non-surgical wearable robotics platform that can support two distinct capability families on one thoraco-pelvic base:

- TALI-H: additional manipulation capability;
- TALI-W: autonomous morphing-flight capability.

The project is not based on permanent biological modification. The human-machine interface is external, removable, instrumented, and designed around explicit structural load paths.

## 2. Core doctrine

### 2.1 Modularity without morphological mixing

TALI-H and TALI-W share TALI-Core, the Universal Thoracic Dock, power, data, safety supervision, user profiles, logging, and training infrastructure. They remain separate modules with different mechanical architectures and verification paths.

### 2.2 Intent-level human interface

The wearer specifies objectives. The controller resolves those objectives into actuator, aerodynamic-surface, force, and trajectory commands while enforcing safety constraints.

For TALI-W, the wearer is not expected to manually coordinate every wing segment, tail surface, propulsor, or landing actuator. Flight-critical stability and terminal landing are autonomous functions.

### 2.3 Recoverability before performance

TALI-W performance is only valid inside a defined and verified Recoverable Flight Envelope (RFE). The controller must preserve a path to a safe state instead of maximizing speed, manoeuvrability, or range at the cost of landing capability.

### 2.4 Aerodynamics first, propulsion second

Normal forward flight should exploit lifting surfaces so that propulsion does not continuously carry the full weight of the human-system combination. Propulsion is primarily an energy-management tool: sustaining flight, climbing, extending glide, providing control margin, and supplying terminal landing authority.

Continuous hover is not the primary cruise regime.

### 2.5 Landing as a state-conversion problem

The desired touchdown is standardized even when the preceding trajectory differs. This is achieved by autonomously converting admissible incoming states into a common Terminal Stabilization State (TSS) before final descent.

This invariance is conditional: only states inside the validated RFE are guaranteed to have a known recovery path. The design does not claim that arbitrary velocity can be cancelled over an arbitrarily short distance.

### 2.6 Layered safety

No single protection mechanism is assumed to make impact harmless. TALI-W safety is layered:

1. prevent unrecoverable flight states;
2. manage aerodynamic energy early;
3. use powered terminal assistance if required;
4. verify TSS before descent;
5. manage contact and load transfer;
6. provide passive residual-energy absorption;
7. retain independent recovery mechanisms during research where practical.

## 3. Research questions

The active programme should answer, in order:

- What total wing area and geometry are required for useful human-scale glide at acceptable wing loading?
- How much of the lifting surface can be made deployable without unacceptable structural or actuation mass?
- Which morphing variables provide the highest control authority per kilogram: span, sweep, camber, twist, leading-edge devices, tail area, or segmented drag surfaces?
- What minimum propulsion authority is needed when aerodynamic braking is used aggressively before terminal landing?
- What entry conditions define the RFE and the terminal landing region?
- Can TSS be reached robustly under sensor uncertainty, gusts, asymmetric actuation, and energy constraints?
- What passive protection is useful after the active system has reduced velocity to the residual design impact envelope?
- What architecture prevents any identified single failure from directly commanding an unsafe touchdown?

## 4. Non-goals at the current stage

The current repository does not claim:

- certified human flight;
- parachute replacement certification;
- safe stopping from arbitrary speed within 5 m;
- exact dock load capacity;
- validated wing area, thrust, battery mass, or landing speed;
- unrestricted human testing;
- regulatory compliance.

Those values and claims require analysis, test evidence, and an applicable regulatory pathway.

## 5. Success definition for the current phase

The current phase succeeds when TALI has:

- traceable requirements;
- a six-degree-of-freedom TALI-W simulation;
- mass and power budgets linked to candidate architectures;
- an executable autonomous landing state machine;
- a quantitative RFE model;
- sub-scale unmanned evidence for morphing-wing control and terminal approach;
- a documented failure and hazard analysis;
- no unsupported performance numbers presented as specifications.
