# TALI-W Propulsion and Energy Architecture

## 1. Role of propulsion

TALI-W propulsion is not currently frozen to a motor, rotor, fan, turbine, or fuel system.

The baseline design principle is:

> Use the wing to provide efficient lift in forward flight; use propulsion to manage energy, climb, extend endurance, preserve control margin, and provide terminal landing authority.

This is intended to avoid the mass and energy penalty of designing the system primarily as a hovering jetpack.

## 2. Candidate architectures

### Large-area foldable propulsors

Potential advantages:

- lower induced-power requirement for a given supported weight when effective disk area is larger;
- electrically controllable;
- useful for short-duration terminal lift and vector control.

Challenges:

- deployment diameter and clearance;
- blade strike hazard;
- structural reaction loads;
- gyroscopic effects;
- folding/locking reliability;
- noise and downwash;
- loss-of-unit asymmetry.

### Compact ducted fans

Potential advantages:

- compact packaging;
- guarded rotor path;
- integration flexibility.

Challenges:

- high disk loading can increase power required for hover/low-speed lift;
- thermal and acoustic load;
- potentially high mass per unit useful thrust.

### Jet/turbine systems

Potential advantages:

- high thrust density;
- compact thrust source.

Challenges:

- hot exhaust;
- fuel/fire risk;
- noise;
- response/control characteristics;
- efficiency and integration near a human;
- demanding failure containment.

### Flapping propulsion

Biologically direct but mechanically demanding at human scale. High cyclic loads, actuator mass, joint fatigue, and control complexity make it a research alternative rather than the current baseline.

## 3. Hover and terminal power

A first-order ideal momentum-theory estimate for induced hover power is:

```text
P_i ~= W^(3/2) / sqrt(2 * rho * A)
```

where `W` is weight and `A` is total effective propulsor disk area.

This relationship motivates studying large effective flow area for terminal lift. Real power will be higher because of propulsive, motor, controller, installation, and interaction losses.

## 4. Important correction: hover energy is not the whole landing problem

A one-second stabilization hold may require relatively little total energy compared with long-duration VTOL. That does **not** mean the complete landing system can use a tiny energy source.

The energy budget must also include:

- kinetic energy removed during terminal arrest;
- climb or go-around reserve;
- actuator energy;
- aerodynamic/propulsive losses;
- peak electrical/mechanical power;
- thermal limits;
- degraded-mode operation;
- required safety reserve.

Peak power and thrust authority may dominate mass even when total hover duration is short.

## 5. Energy-aware flight envelope

Remaining usable energy is part of the RFE. The controller must not commit to a landing/flight state that leaves insufficient energy for the required terminal sequence plus allocated reserve.

The energy estimator shall account for temperature, battery/fuel state, voltage/power limits, propulsion health, and uncertainty appropriate to the selected technology.

## 6. Trade-study metrics

Each propulsion candidate should be scored against:

- installed mass;
- peak thrust;
- continuous thrust;
- thrust-to-mass ratio;
- effective disk/flow area;
- peak power;
- total mission energy;
- deployment volume;
- control bandwidth;
- redundancy options;
- thermal hazard;
- acoustic/downwash hazard;
- failure containment;
- human proximity;
- integration with wing/tail flow;
- maintainability.

No propulsion topology should be declared baseline until this trade is tied to a complete mass and landing-energy model.
