# TALI System Architecture

Version: 0.2.0

## 1. Top-level decomposition

```text
Human wearer
     |
     | intent + physiological / interface signals
     v
+---------------------------+
|        TALI-Core          |
|---------------------------|
| safety supervisor         |
| power/data distribution   |
| state/health aggregation  |
| logging                   |
| module recognition        |
| wearer interface          |
+-------------+-------------+
              |
       Universal Thoracic Dock
              |
      +-------+-------+
      |               |
      v               v
   TALI-H           TALI-W
 manipulation     flight system
```

TALI-Core is the common integration layer. TALI-H and TALI-W have separate mission computers where required, but safety-critical interlocks and module-state supervision are visible to the core.

## 2. TALI-Core responsibilities

TALI-Core shall provide:

- posterior thoraco-pelvic structural load transfer;
- adjustable human interface and pressure distribution;
- module attachment and release interfaces;
- shared power and data buses;
- independent safety supervision;
- emergency-state signalling;
- module identification and configuration control;
- central event and sensor logging;
- system-health indication;
- candidate/wearer calibration storage.

TALI-Core shall not assume a historical dock diameter, load rating, connector type, or emergency-release force until those values are derived and verified.

## 3. Universal Thoracic Dock

The UTD is an interface standard, not a single frozen geometry at this stage.

Required interface classes:

- structural load path;
- keyed mechanical alignment;
- positive lock state sensing;
- power;
- deterministic data link;
- module identity;
- load/strain sensing;
- safety interlock;
- controlled release and maintenance release;
- optional fluid or pneumatic services if a validated module requires them.

A module shall not receive flight- or force-capable authority until the dock lock state and module identity are verified.

## 4. TALI-H architecture

TALI-H uses compact articulated auxiliary arms. The control allocation prioritizes manipulation and compliant contact rather than flight.

Functional blocks:

```text
intent -> task planner -> collision/force supervisor -> arm controller
                                            |
                                 joint + force sensing
                                            |
                                      end effector
```

TALI-H remains outside the detailed scope of the TALI-W flight documents.

## 5. TALI-W architecture

TALI-W is a wearable autonomous aircraft module.

```text
                    wearer intent
                         |
                         v
               mission / mode manager
                         |
                         v
+---------------------------------------------------+
|          autonomous flight-control system         |
|---------------------------------------------------|
| state estimation                                  |
| RFE / reachability monitor                        |
| guidance / trajectory management                  |
| attitude + rate control                           |
| aerodynamic control allocation                    |
| propulsion control allocation                     |
| terminal landing manager                          |
| fault detection / isolation / accommodation       |
+----+------------------+-------------------+--------+
     |                  |                   |
     v                  v                   v
morphing wings      tail / drag         propulsion
     |               surfaces               |
     +------------------+--------------------+
                        |
                     vehicle
                        |
       IMU / air data / loads / terrain / health
                        |
                        +--------------------> estimator
```

## 6. TALI-W flight states

Minimum state-machine set:

1. `SAFE_STOWED`
2. `DEPLOY_CHECK`
3. `GLIDE`
4. `POWERED_FORWARD_FLIGHT`
5. `APPROACH_ENERGY_MANAGEMENT`
6. `FLARE`
7. `TERMINAL_ARREST`
8. `TERMINAL_STABILIZATION`
9. `CONTROLLED_DESCENT`
10. `CONTACT_LOAD_TRANSFER`
11. `LANDED_SAFE`
12. `RECOVERY_ABORT`
13. `EMERGENCY_SURVIVAL`

Transitions shall be condition-based rather than time-only. Each transition requires sensor confidence and system-health gates appropriate to the function.

## 7. Human authority

During ordinary flight, the human may request high-level direction or mode changes within the permitted envelope.

During the committed terminal landing sequence:

- detailed control is autonomous;
- human action is not required to maintain stability;
- a human command cannot force touchdown while the safety gate is false;
- an abort/recovery request may be accepted when the controller determines that it improves or preserves safety.

## 8. Landing architecture

The terminal landing architecture uses two formal concepts:

### Recoverable Flight Envelope (RFE)

A set of system states from which the controller has a verified path to an acceptable safe state under the defined disturbance and failure assumptions.

The RFE depends on more than speed and altitude. It may include:

- position and velocity;
- attitude and angular rate;
- wing configuration;
- available aerodynamic authority;
- available thrust and actuator authority;
- remaining energy;
- terrain suitability;
- wind/gust estimate;
- system-health state.

### Terminal Stabilization State (TSS)

A verified pre-touchdown state in which translational velocity, vertical descent rate, angular rates, attitude, terrain confidence, energy margin, and system health satisfy the touchdown-entry criteria.

Final descent is inhibited until TSS is true.

## 9. Structural integration

Flight loads must be evaluated as full-body inertial and aerodynamic loads, not merely auxiliary-arm joint loads. The TALI-Core/UTD/TALI-W load path therefore requires separate flight structural analysis covering:

- symmetric and asymmetric wing loads;
- gust and manoeuvre loads;
- flare and arrest loads;
- propulsion reaction loads;
- failed/stuck surface loads;
- landing/contact loads;
- deployment and locking transients;
- emergency recovery loads.

## 10. Configuration control

Each hardware and software build should record:

- module revision;
- geometry revision;
- mass properties;
- centre of gravity;
- actuator/propulsor configuration;
- firmware/software commit;
- flight-envelope version;
- requirement baseline;
- test restrictions.

No flight result is valid without the associated configuration record.
