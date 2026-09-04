# TALI-W Flight Dynamics Notes

## 1. Purpose

This file defines the minimum physical model needed before performance claims are converted into hardware requirements.

## 2. Aerodynamic force model

First-order lift and drag relations are:

```text
L = 0.5 * rho * V^2 * S * C_L
D = 0.5 * rho * V^2 * S * C_D
```

where:

- `rho` = air density;
- `V` = airspeed;
- `S` = reference area;
- `C_L` = lift coefficient;
- `C_D` = drag coefficient.

These relations explain why a fixed wing loses useful aerodynamic force rapidly as airspeed approaches zero. A one-second stationary stabilization phase cannot be obtained from a fixed wing alone in still air. It requires active air acceleration (for example a propulsor or flapping mechanism), ground effect/cushion interaction, or some other supporting force.

## 3. Wing loading

Wing loading is:

```text
W/S
```

Lower wing loading generally supports lower characteristic flight speed, at the cost of larger surface area and structure. TALI-W therefore has a central mass-area trade: large lightweight deployable surfaces are valuable only if their structure, deployment mechanisms, and control system do not erase the aerodynamic benefit.

No wing-area value is fixed in this repository until a complete mass model and target speed envelope are defined.

## 4. Energy model

Translational kinetic energy is:

```text
E_k = 0.5 * m * |V|^2
```

Potential energy relative to a reference is:

```text
E_p = m * g * h
```

A flare can exchange kinetic and potential energy while aerodynamic drag dissipates mechanical energy. It cannot eliminate the need to account for total energy and structural/physiological acceleration limits.

## 5. Stopping distance

For a simplified constant deceleration:

```text
a = (v_i^2 - v_f^2) / (2 * d)
```

This is why the final 5 m cannot be specified as the complete braking distance for arbitrary high-speed flight. The controller must start energy management earlier as required by the incoming state.

## 6. Six-degree-of-freedom model

The simulation shall include at minimum:

- translational position and velocity;
- roll, pitch, yaw attitude;
- angular rates;
- gravity;
- aerodynamic forces and moments;
- control-surface / morphing effects;
- propulsion forces and moments;
- changing mass properties if deployment changes inertia;
- wind and gust disturbances;
- ground/terrain geometry for terminal tests.

The model should support parameter uncertainty so that the RFE is not computed from an unrealistically exact vehicle.

## 7. Morphing and stability

Morphing changes more than lift and drag. Extending/folding wing segments changes inertia, aerodynamic centre, stability margin, and control effectiveness. Flight-control design must therefore treat configuration as part of the vehicle state.

A safe controller should not assume that one set of gains applies across stowed, high-speed, high-lift, flare, and terminal configurations.

## 8. Landing invariance

The desired research property is:

```text
varied admissible approach states
             |
             v
autonomous state conversion
             |
             v
common bounded TSS
             |
             v
repeatable touchdown state
```

This is not true mathematical invariance for arbitrary initial conditions. It is a verified convergence property for the defined RFE.

## 9. Simulation outputs required before hardware freeze

- trim maps versus speed and configuration;
- lift/drag polars with uncertainty;
- stall/high-angle-of-attack behavior;
- control authority maps;
- glide ratio and sink-rate maps;
- powered-flight energy requirement;
- flare trajectories;
- terminal arrest energy/power;
- RFE boundaries;
- sensitivity to gusts and sensor delay;
- load envelopes for structure and UTD.
