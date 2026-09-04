# TALI-W Autonomous Terminal Landing

## 1. Objective

Create a landing sequence in which the final touchdown state is repeatable and minimally dependent on the preceding trajectory **provided the approach state is inside the validated Recoverable Flight Envelope (RFE)**.

The system does not claim to neutralize arbitrary incoming momentum in the final 5 m.

## 2. Key distinction

The final 5 m, or any later selected altitude, is a **terminal landing region**. It is not the complete braking distance.

High-speed energy management may begin tens or hundreds of metres earlier depending on speed, wing performance, thrust authority, wind, terrain, and human acceleration limits.

## 3. State sequence

```text
FLIGHT
  |
  v
LAND_REQUEST
  |
  v
APPROACH_ENERGY_MANAGEMENT
  |
  | verify RFE margin / terrain / energy
  v
LAND_COMMIT
  |
  v
AUTOMATIC_FLARE
  |
  v
TERMINAL_ARREST
  |
  v
TERMINAL_STABILIZATION_STATE (TSS)
  |
  | nominal hold ~1 s; final value TBD
  v
CONTROLLED_DESCENT
  |
  v
CONTACT_DETECTION
  |
  v
CONTROLLED_LOAD_TRANSFER
  |
  v
LANDED_SAFE
```

At multiple points, failure to satisfy the entry condition routes to `RECOVERY_ABORT` instead of continuing downward.

## 4. Terminal Stabilization State

TSS is a Boolean safety gate backed by continuous quantitative margins.

Candidate TSS criteria include:

- horizontal speed below `TBD`;
- vertical speed inside `TBD`;
- roll/pitch/yaw attitude inside `TBD`;
- angular rates below `TBD`;
- terrain-relative position/clearance acceptable;
- landing surface confidence above `TBD`;
- wing/landing configuration verified;
- propulsion/control reserve above `TBD`;
- energy reserve above `TBD`;
- no incompatible critical fault active.

The numerical values must come from simulation, human tolerance, structural capability, and unmanned testing.

## 5. One-second stabilization hold

The current concept uses approximately one second of stabilized support before final contact because this creates a clear separation between high-energy flight and low-energy touchdown.

The hold is not assumed to be exactly one second in the final design. It may be shortened or lengthened after control, gust, energy, and human-factor analysis.

The important invariant is:

> Final descent starts from a verified stable state rather than being a continuation of the high-speed trajectory.

## 6. Touchdown gate

The system shall implement a logic equivalent to:

```text
if TSS == TRUE and terrain_valid == TRUE and reserve_ok == TRUE:
    permit CONTROLLED_DESCENT
else:
    inhibit touchdown
    execute hold / re-position / go-around / recovery as physically available
```

The actual flight code must be deterministic, verified, and independent of unvalidated high-level AI outputs.

## 7. Trajectory convergence requirement

Testing should define a matrix of approach states inside the RFE:

- different horizontal speeds;
- different descent rates;
- different headings;
- different lateral offsets;
- different permissible attitudes;
- gust/wind cases;
- selected degraded-mode cases.

Success is not that all trajectories look identical. Success is that they converge to a bounded TSS and touchdown distribution within the validated limits.

## 8. Powered terminal assist

Terminal propulsion may provide:

- final horizontal-velocity cancellation;
- vertical support during the TSS hold;
- attitude control when aerodynamic authority is low;
- small terrain-relative repositioning;
- controlled descent;
- go-around/recovery margin.

The preferred design minimizes how much kinetic energy must be removed by propulsion by performing aerodynamic braking first.

## 9. Ground-effect / cushion research

A near-ground inflatable skirt or air-cushion concept may be investigated as a **supplemental** terminal support/impact-management mechanism. It is not assumed to replace free-air control before surface proximity is verified.

Any ground-cushion concept must address:

- uneven/porous terrain;
- lateral motion;
- skirt snagging;
- crosswind;
- pressure loss;
- debris/downwash;
- transition from free-air support to cushion support.

## 10. Abort philosophy

A safe landing system needs a decision boundary before it runs out of options.

If the controller predicts that TSS cannot be reached with required margin, it must not continue nominal descent simply because the ground is near. Depending on the architecture and remaining capability, recovery may mean:

- re-accelerate into forward flight;
- climb;
- extend the approach;
- divert to another surface;
- enter a separate emergency recovery system;
- prepare passive survival configuration when no active recovery remains.

## 11. Verification metrics

Record at minimum:

- initial approach state;
- RFE margin;
- flare start state;
- peak accelerations and loads;
- terminal propulsion impulse/energy;
- time to TSS;
- TSS hold stability;
- touchdown velocities and angular rates;
- touchdown position dispersion;
- landing-structure loads;
- recovery success when TSS is intentionally made unreachable.
