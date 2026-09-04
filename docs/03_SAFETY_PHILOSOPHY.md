# TALI Safety Philosophy

Version: 0.2.0

## 1. Safety objective

TALI-W is a human-carrying flight research concept. The correct safety objective is not "make unsafe landing impossible." No engineered system can guarantee that under arbitrary failures, energy states, terrain, weather, or structural damage.

The engineering objective is instead:

> Prevent the controller from intentionally entering a touchdown state unless predefined safety conditions are satisfied, preserve a recovery path while one remains physically available, and prevent identified single failures from directly causing uncontrolled touchdown wherever practicable.

## 2. Physics boundary

Landing energy cannot be eliminated by software, gel, foam, or a capsule.

Kinetic energy is:

```text
E_k = 0.5 * m * v^2
```

A simple constant-deceleration stopping-distance relationship is:

```text
d = (v_i^2 - v_f^2) / (2 * a)
```

Therefore, increasing speed rapidly increases both the energy to be removed and the distance required for a given allowable deceleration. The final 5 m cannot be treated as a universal stopping distance from arbitrary high-speed flight.

## 3. Safety layers

### Layer 1 - Design envelope

Define allowable mass, centre-of-gravity range, aerodynamic configurations, weather, energy state, terrain class, and system-health conditions. Operation outside that envelope is not an intended mode.

### Layer 2 - Recoverable Flight Envelope protection

The controller continuously estimates whether a safe terminal state remains reachable. Performance commands are constrained before the state becomes unrecoverable.

### Layer 3 - Early energy management

Use aerodynamic drag, lift-vector management, configuration change, path shaping, and flare early enough that the terminal region is entered with sufficient margin.

### Layer 4 - Active terminal control

Use available aerodynamic and powered control authority to reduce residual translational and rotational motion and establish TSS.

### Layer 5 - Touchdown gate

The final-descent command is inhibited unless the TSS criteria are verified. Terrain confidence, remaining control authority, and remaining energy are part of the gate.

### Layer 6 - Controlled load transfer

Touchdown includes contact detection and a controlled transition of load from flight hardware to landing structure and the human-support frame.

### Layer 7 - Passive residual-energy protection

Inflatable cells, controlled venting, crush structures, compliant landing members, harness stroke, and load spreading may reduce residual loads. They are designed for a bounded impact envelope and must not be described as protection from arbitrary impact speed.

### Layer 8 - Independent recovery during research

Sub-scale and full-scale test programmes should use independent recovery and termination systems appropriate to the article. Occupied research, if ever authorized, should retain conventional independent recovery where technically applicable until equivalent evidence exists for the integrated system.

## 4. Safety-critical autonomy

The terminal landing controller must not rely on continuous human input. After `LAND_COMMIT`, the system is responsible for:

- trajectory management;
- flare timing;
- speed/energy reduction;
- attitude and rate stabilization;
- terrain validation;
- TSS determination;
- descent-rate control;
- contact detection;
- load transfer;
- abort/recovery decisions.

Human intent may request recovery but may not bypass a false touchdown-safety gate.

## 5. Single-failure philosophy

A formal Functional Hazard Assessment (FHA) and Preliminary System Safety Assessment (PSSA) are required before occupied flight. The target architecture should ensure that no identified single failure with credible occurrence can directly create an uncontrolled touchdown without an independent mitigating path.

Examples requiring analysis include:

- one IMU producing erroneous attitude data;
- altimeter/range sensor failure;
- loss of one propulsor;
- one wing actuator jam;
- asymmetric wing deployment;
- loss of a power bus;
- flight-computer fault;
- battery cell or pack fault;
- loss of air-data sensing;
- false terrain classification;
- dock-lock sensor disagreement;
- structural overload or damage indication.

## 6. Research safety references

TALI is not claiming certification to aerospace standards. However, the project should borrow development-assurance practices from current aviation guidance where useful, including requirements validation/verification, systematic safety assessment, independence for high-criticality verification, configuration control, and failure-condition analysis.

Candidate reference families include SAE ARP4754B for aircraft/system development and ARP4761A for safety assessment, plus RTCA DO-178C/DO-254 concepts if safety-critical airborne software or electronic hardware reaches a certification-oriented stage.

These references guide process discipline; applicability and regulatory basis must be determined separately for any future certified vehicle category.
