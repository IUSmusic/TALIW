# TALI-W Passive Landing Protection

## Purpose

Passive protection is the last layer after the active flight system has already reduced energy to a bounded residual impact condition.

It is not a substitute for aerodynamic braking, propulsion, or autonomous landing control.

## Why gel alone cannot solve arbitrary impact

Impact energy scales with velocity squared:

```text
E_k = 0.5 * m * v^2
```

A passive material can only reduce peak force by deforming, flowing, crushing, venting, or otherwise increasing the stopping time and distance. A fixed-thickness gel or capsule eventually bottoms out. At that point the remaining velocity must be removed over very little distance.

Therefore no fixed wearable gel/capsule can safely absorb arbitrary mass and speed.

## Candidate layered protection

A useful landing-survival package may combine:

1. **Compliant first contact** - feet, skids, pads, or deployable members that establish controlled contact.
2. **Long-stroke structure** - telescoping, crushable, pneumatic, hydraulic, elastomeric, or other energy-absorbing members.
3. **Controlled-vent air cells** - inflatable volume that spreads load and dissipates energy through regulated venting.
4. **Crush structures** - sacrificial honeycomb or cellular elements for abnormal residual impacts.
5. **Harness stroke** - allow the outer structure to decelerate while the human body travels through a longer controlled path.
6. **Load spreading** - distribute force through the pelvis, torso support, and other designed interfaces rather than concentrating load locally.

## Design requirement

Passive protection must be specified against a residual impact envelope such as:

```text
mass range: TBD
vertical impact speed: TBD
horizontal residual speed: TBD
attitude range: TBD
surface class: TBD
```

Those values must be derived from the active landing controller's verified worst-case residual state plus uncertainty and failure cases.

## Capsule concept

A deployable capsule can still be valuable if its role is correctly bounded:

```text
high-speed flight
    -> active aerodynamic / powered reduction
    -> low-energy abnormal touchdown envelope
    -> deployable air/crush capsule
    -> reduced occupant load
```

This architecture is far more realistic than asking the capsule to stop the original high-speed flight state.

## Ground cushion concept

Near the ground, an inflated skirt or controlled air cushion may increase effective stopping distance and distribute load. Its feasibility depends strongly on surface leakage, ground roughness, lateral velocity, skirt geometry, and blower/pressure requirements.

It should be tested as a landing aid and passive/semipassive protection layer, not assumed to create a universal hover state.

## Verification

Use instrumented surrogate mass/inertia before human exposure. Measure:

- acceleration time history;
- pelvis/chest/head surrogate loads;
- stroke used;
- pressure distribution;
- bottom-out margin;
- rebound;
- lateral stability;
- performance after one or more failed cells/elements where applicable.
