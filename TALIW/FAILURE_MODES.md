# TALI-W Preliminary Failure Modes

Status: preliminary hazard-identification input, not a completed FHA/FMEA.

| Failure / hazard | Potential effect | Required design response / research question |
|---|---|---|
| IMU erroneous attitude | incorrect stabilization command | redundant/diverse state estimation, reasonableness checks, isolation |
| Range/altitude sensor loss | incorrect ground-relative descent | sensor diversity, minimum-confidence gate, abort/recovery |
| Air-data error | stall/flare error, incorrect RFE | estimator cross-checks, conservative degraded envelope |
| Vision/terrain misclassification | unsafe landing surface selection | independent range/geometry checks, terrain-confidence gate |
| One wing actuator jam | asymmetric lift/drag/moment | detect jam, control reallocation, restricted envelope/recovery |
| Incomplete/asymmetric wing deployment | major control imbalance | lock/configuration sensing, inhibit progression, recovery state |
| Structural overload/damage | loss of wing or control | load monitoring where useful, conservative limits, independent recovery |
| One propulsor loss | reduced terminal lift/control | topology-specific redundancy, reallocation, minimum remaining authority |
| Propulsor stuck high/low | uncontrolled force/moment | independent shutdown/isolation, counter-authority assessment |
| Main power bus loss | loss of actuation/control | segregated safety power / reserve architecture as required by hazard analysis |
| Battery thermal event | fire, power loss | containment, isolation, monitoring, emergency landing/recovery |
| Flight computer fault | erroneous or absent control | monitored redundant lanes / dissimilar safety monitor as justified |
| Software state-machine error | unsafe transition | deterministic requirements, verification, transition guards, HIL testing |
| Corrupted configuration | wrong limits/gains | signed/configuration-controlled data, startup validation |
| UTD unlock or false lock state | structural separation | positive mechanical lock, independent sensing, no authority if uncertain |
| Excess wind/gust | loss of RFE margin | environmental envelope, online margin reduction, abort before terminal commit |
| Energy below estimate | terminal arrest unavailable | conservative estimator, reserve policy, landing-commit gate |
| Human incapacitation | no pilot response | autonomous stability/landing should not require continuous input |
| Human unsafe command | request outside envelope | command limiting; no touchdown bypass |
| Landing surface unavailable late | no safe contact location | terrain assessment early, divert/go-around reserve |
| Passive absorber fails/bottoms out | increased occupant load | bounded residual envelope, multiple layers, surrogate testing |
| Sensor common-mode failure | multiple incorrect channels | diversity and independence analysis, not redundancy by duplication alone |

## Required safety analyses before occupied free flight

- Functional Hazard Assessment (FHA)
- Preliminary System Safety Assessment (PSSA)
- FMEA/FMECA as appropriate
- Fault-tree analysis for catastrophic/hazardous outcomes
- Common-cause/common-mode analysis
- zonal/installation hazard analysis
- energy and thermal hazard analysis
- software/hardware development assurance planning

The final choice of methods depends on the selected architecture and regulatory basis.
