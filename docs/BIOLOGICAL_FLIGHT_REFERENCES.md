# Biological Flight References for TALI-W

## Purpose

TALI-W uses functional biomimicry. No single bird is treated as a complete blueprint for a human-scale aircraft.

## Kori bustard - large-body flight reference

The Kori bustard remains relevant because adult males are among the heaviest living flying birds. It is a useful qualitative reference for large-body take-off, broad wing loading constraints, and folding geometry.

Engineering caution: a 10-20 kg bird does not scale directly to a human-system mass. Structural dimensions, Reynolds number, muscle/actuator power, inertial scaling, and wing loading change substantially.

Reference:
- Smithsonian's National Zoo, "Kori bustard": https://nationalzoo.si.edu/animals/kori-bustard

## Wing morphing - stability and agility

Birds alter wing configuration to change aerodynamic and inertial properties. This supports the TALI-W research direction of treating span/fold/sweep/configuration as part of flight control rather than as simple deployment animation.

Reference:
- Harvey, C. et al. (2022), "Birds can transition between stable and unstable states via wing morphing," Nature 603, 648-653. https://doi.org/10.1038/s41586-022-04477-8

## Alula - high-angle-of-attack flow control

The alula is particularly relevant to landing/slow-flight research. Experimental work has shown lift enhancement and stall-delay effects associated with an alula-generated vortex at high angle of attack.

Reference:
- Lee, S. et al. (2015), "The Function of the Alula in Avian Flight," Scientific Reports 5, 9914. https://doi.org/10.1038/srep09914

## Fan tail - low-speed control hypothesis

Bird tails can alter stability, trim, drag, and manoeuvring forces. TALI-W should evaluate a deployable tail against equivalent control surfaces rather than assuming a literal feathered tail is optimal.

Research questions:

- How much pitch/yaw authority is produced per unit tail mass and area?
- Does the tail remain effective in the wake of the human body and main wing?
- Can the tail reduce wing actuator authority requirements during flare?
- Is a split or differential tail more mass-efficient?

## Raptors / perching flight - flare and braking

Landing birds often combine increased wing area, high angle of attack, body pitch change, tail deployment, and rapid control adjustment. TALI-W should reproduce the *functions* of this sequence with mechanically appropriate surfaces and autonomous control.

The project should acquire quantitative perching/landing trajectory data before choosing flare limits or copying a specific species.

## Scaling rule

Biological observation can generate hypotheses. It does not establish a human-scale requirement.

Every biomimetic feature must pass the same engineering test:

```text
Does this feature improve verified flight/landing performance
by enough to justify its mass, complexity, failure modes, and stowage volume?
```
