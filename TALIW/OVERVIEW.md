# TALI-W Overview

## Definition

TALI-W is the flight-directed module of Project TALI: a wearable, deployable, morphing aerodynamic system intended to investigate controlled human-scale glide, powered forward flight, autonomous flight-envelope management, and automated terminal landing.

TALI-W is not intended to reproduce a bird anatomically. It translates selected aerodynamic functions into engineered mechanisms.

## Design hypothesis

The mass-efficient architecture is expected to be hybrid:

```text
large aerodynamic surfaces
        +
morphing/high-lift/high-drag control
        +
modest propulsion for energy management
        +
high-authority short-duration terminal assist
        +
passive residual-impact protection
```

The design deliberately avoids making continuous hover the normal flight condition.

## Functional flight modes

### Stowed / ground mode

Wings and terminal devices are mechanically safe, restrained, and monitored.

### Deployment

The system verifies clearance, lock state, symmetry, actuator health, and configuration before enabling the next flight mode.

### Glide

The wings provide lift while gravitational potential energy supplies the net energy loss. Propulsion may be off or at low authority.

### Powered forward flight

The wing continues to provide the majority of normal lift while propulsion offsets drag and, when required, supplies climb energy.

### Approach energy management

The controller trades speed, altitude, drag, lift vector, path length, and available propulsion authority to enter the terminal region inside the RFE.

### Flare

The controller increases angle of attack and/or redirects the lift vector to reduce descent and forward speed while respecting stall and structural margins.

### Terminal arrest

Residual velocity and angular motion are reduced using the combination of available aerodynamic control and terminal propulsion.

### Terminal Stabilization State

The system establishes the bounded state required before controlled final descent.

### Controlled descent and contact

The controller manages descent, detects contact, and transitions load to the landing/human-support structure.

### Recovery / abort

If the landing state cannot be verified, the controller selects a predefined recovery action compatible with remaining physical capability.

## Biomimetic functions

Candidate biological inspirations are mapped by function:

- large terrestrial flying birds -> large-body structural/aerodynamic reference;
- soaring birds -> efficient high-aspect-ratio glide principles;
- raptors and perching birds -> flare and rapid aerodynamic braking;
- alula -> high-angle-of-attack flow control;
- fan tails -> pitch/yaw authority and low-speed area increase;
- wing morphing across species -> stability/agility management.

The Kori bustard remains a useful large-bird reference but is not the sole aerodynamic template.

## Interfaces to TALI-Core

TALI-W requires the UTD/TALI-Core to provide:

- structural root attachment and load transfer;
- power and energy-state reporting;
- deterministic data;
- module identification;
- independent safety supervision;
- emergency state signalling;
- human-interface data;
- logging.

The final structural architecture may require additional load paths beyond the conceptual thoracic root ports. Those paths must be derived from full-scale aerodynamic and landing loads rather than assumed from auxiliary-arm geometry.

## Current unknowns

The following are intentionally not frozen:

- wing area and span;
- wing aspect ratio;
- maximum system mass;
- minimum/maximum flight speed;
- structural design speed;
- terminal region altitude;
- TSS velocity limits;
- propulsion topology;
- propulsor area and thrust;
- battery chemistry/capacity;
- landing energy absorber geometry;
- exact UTD geometry and rating.

These become requirements only after modelling and verification justify them.
