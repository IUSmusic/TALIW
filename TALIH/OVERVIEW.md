# TALI-H Overview

## Definition

TALI-H is the manipulation-directed auxiliary hand-arm module of Project TALI. It remains separate from TALI-W and is not a flight surface.

## Intended functions

TALI-H investigates additional-arm capability for:

- holding and stabilizing objects while the biological hands remain free;
- gripping and clamping;
- tool positioning;
- machinery or fixture interaction;
- passing/receiving objects;
- quadrimanual coordination research;
- external bracing/support within verified load limits.

## Mechanical principles

The preferred architecture uses compact articulated arms attached through the UTD with heavy actuation kept proximal where practical. Candidate features include:

- modular wrists;
- interchangeable end effectors;
- joint encoders;
- force/torque or load sensing;
- compliant contact control;
- mechanical resting/holding locks where beneficial;
- collision-aware trajectories;
- fold-away rest geometry.

No joint count, payload, reach, or force rating is frozen until a specific prototype configuration is documented and tested.

## Control philosophy

The wearer provides intent-level commands such as:

```text
hold
release
grip
brace
stabilize
move endpoint
pass object
```

The onboard controller manages detailed joint coordination, force limits, collision avoidance, and grasp behavior.

Candidate human-input channels may include foot/toe input, sEMG, torso/limb gesture, gaze/head targeting, buttons, or other non-surgical interfaces. Safety-critical force limits are enforced by the machine rather than relying on operator precision.

## Relationship to TALI-Core

TALI-H uses the shared thoraco-pelvic load path, power/data infrastructure, safety supervision, module identity, and logging. Its load cases and verification plan remain separate from TALI-W flight load cases.
