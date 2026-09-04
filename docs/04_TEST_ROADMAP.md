# TALI Verification and Test Roadmap

Version: 0.2.0

## Principle

TALI-W shall be developed by increasing energy and human exposure only after the preceding stage produces traceable evidence. A visually successful demonstration is not a substitute for measured margins and repeatability.

## Phase 0 - Requirements and modelling

Deliverables:

- controlled requirement baseline;
- mass-properties model;
- aerodynamic model with uncertainty bounds;
- six-degree-of-freedom simulation;
- propulsion/energy model;
- terminal landing state machine;
- preliminary RFE estimator;
- hazard log and preliminary FHA;
- test instrumentation plan.

Exit criteria:

- no undefined safety-critical state transition;
- simulation can reproduce nominal glide, approach, flare, terminal stabilization, controlled descent, and abort;
- energy and stopping-distance constraints are explicitly modelled.

## Phase 1 - Component benches

Test separately:

- wing deployment and locking;
- structural members and joints;
- control-surface actuators;
- candidate propulsors;
- power electronics;
- sensors and timing;
- landing energy absorbers;
- UTD locking and load sensing;
- software hardware-in-the-loop interfaces.

Exit criteria:

- measured component properties replace assumed values in the models;
- failure states are characterized;
- no critical component is accepted only from catalogue performance.

## Phase 2 - Sub-scale unmanned aerodynamic demonstrator

Objectives:

- validate morphing-wing aerodynamics;
- measure stall/high-angle-of-attack behavior;
- test tail/leading-edge devices;
- demonstrate autonomous glide and flare;
- evaluate RFE logic at low energy;
- test recovery-state transitions.

No human-carrying structure is required at this stage.

## Phase 3 - Sub-scale terminal landing demonstrator

Objectives:

- approach from varied headings and speeds inside a defined test envelope;
- autonomously converge to one terminal state;
- demonstrate touchdown inhibition when TSS criteria are not met;
- demonstrate abort/recovery behavior;
- quantify terminal position, velocity, attitude, and energy repeatability.

This phase specifically tests the claim that preceding trajectory can be made largely irrelevant to final touchdown **within the validated RFE**.

## Phase 4 - Full-scale unmanned mass simulator

Use an instrumented anthropomorphic mass/inertia surrogate.

Objectives:

- validate full-scale structural loads;
- verify TALI-Core/UTD load transfer;
- verify full-scale deployment dynamics;
- validate propulsion and energy margins;
- test passive residual-impact protection;
- test terminal landing under representative mass properties;
- exercise sensor and actuator faults.

## Phase 5 - Tethered integrated system

Objectives:

- validate human-interface ergonomics separately from free flight;
- verify that the system can stabilize without continuous personal input;
- test control transfer, abort requests, and safe shutdown;
- measure harness pressure, motion, and load transfer;
- perform low-energy suspension/assisted-lift experiments.

Tethering must not be used to conceal an unstable controller; free-flight-equivalent dynamics should be identified and modelled.

## Phase 6 - Independent design and safety review

Before considering occupied free flight, obtain independent review of:

- structural substantiation;
- flight-control architecture;
- software assurance;
- propulsion and energy safety;
- FHA/PSSA and fault trees;
- RFE definition;
- emergency recovery;
- environmental limits;
- test evidence and unresolved anomalies.

## Phase 7 - Human-carrying research, only if justified

No occupied high-energy landing test should be the first demonstration of a new landing function.

Any future human-carrying programme should begin at the lowest practical energy and retain independent recovery systems where feasible. Test expansion should be incremental and based on measured margins, not expectation.

## Evidence structure

Every test record should include:

- test ID and date;
- article configuration ID;
- software commit;
- requirement IDs under test;
- environmental conditions;
- instrumentation and calibration;
- planned limits and automatic termination conditions;
- actual results;
- anomalies;
- pass/fail disposition;
- links to raw data.
