# TALI-W Autonomous Flight Control

## 1. Control philosophy

The human is a mission-level input, not the inner-loop flight controller.

Example intent commands:

```text
forward / heading request
turn request
climb / descend request
speed preference
land request
recover / abort request
```

The flight computer converts intent into physically admissible trajectories and actuator commands while maintaining envelope and safety constraints.

## 2. Control hierarchy

```text
wearer intent
    |
mission manager
    |
guidance / trajectory manager
    |
RFE + constraint supervisor
    |
6-DOF flight controller
    |
control allocator
    +----------------------+----------------------+
    |                      |                      |
wing morphing         tail/drag surfaces     propulsion
```

The safety supervisor may override lower-priority mission requests.

## 3. State estimation

Candidate sensor classes include:

- redundant IMUs;
- airspeed / pressure sensing;
- GNSS where available;
- radar or lidar range/altitude sensing;
- optical/vision terrain-relative sensing;
- wing joint/configuration encoders;
- load/strain sensing;
- propulsor speed/current/thrust estimation;
- battery/energy sensors;
- TALI-Core/UTD load and lock sensing.

No single sensor modality should be assumed sufficient for a catastrophic flight function without hazard analysis.

## 4. RFE monitor

The RFE monitor estimates whether one or more safe target states remain reachable under the current constraints.

Inputs may include:

```text
position + terrain
velocity + wind
attitude + rates
wing configuration
control authority
propulsion health
energy reserve
structural/load margins
sensor confidence
```

The initial implementation may use conservative precomputed reachable sets or lookup envelopes. Later versions may use online model-predictive reachability if computation, verification, and timing allow.

## 5. Landing takeover

After `LAND_COMMIT`, terminal landing becomes an autonomous safety-critical sequence.

The user does not manually time the flare, manage propulsor balance, or decide the instant of touchdown. The system may accept a recovery request, but cannot accept a command that bypasses TSS.

## 6. Terminal controller

The terminal controller should control at least:

- horizontal velocity;
- vertical velocity;
- roll/pitch/yaw attitude;
- roll/pitch/yaw rates;
- terrain-relative position;
- remaining energy margin;
- landing-system configuration.

It may use model-predictive control, nonlinear control, gain-scheduled control, or another architecture. The specific algorithm is not yet baselined.

## 7. Fault detection, isolation, accommodation

Safety-critical autonomy requires explicit handling of disagreement and failure.

Examples:

- compare redundant inertial/range sources;
- reject or isolate implausible sensor lanes;
- reallocate control after actuator/propulsor loss;
- constrain manoeuvres after structural/load warnings;
- enter recovery if the TSS is no longer reachable;
- prevent a single corrupted operator input from commanding an unsafe trajectory.

## 8. Local autonomy

Flight-critical control shall not depend on cloud connectivity, remote internet access, or external AI services. External systems may support planning, telemetry review, simulation, or non-critical assistance but loss of connection must not remove flight stabilization or landing authority.

## 9. Logging

Minimum event logging should include:

- estimated state;
- raw or health-relevant sensor data;
- mode transitions;
- RFE margin/decision variables;
- TSS gate state;
- operator intents;
- actuator/propulsor commands;
- energy state;
- faults and reconfiguration;
- software/configuration IDs.
