# Universal Thoracic Dock (UTD)

## Status

Interface concept active; exact geometry and numeric ratings TBD.

The legacy concept diagram is archived and must not be treated as a validated specification.

## Required interface functions

The UTD shall provide or support:

- mechanical alignment;
- positive structural locking;
- independent lock-state sensing;
- module identity;
- power interface;
- deterministic data interface;
- safety interlock;
- load/strain monitoring where useful;
- controlled maintenance release;
- emergency-state handling;
- optional pneumatic/fluid services only if a validated architecture requires them.

## Flight-specific issue

TALI-W may create loads and moments substantially larger and more dynamic than TALI-H. The final flight module may therefore require a root interface or distributed structural attachment that extends beyond the visual form of the original circular thoracic dock concept.

The UTD should be treated as an **interface standard** whose mechanical implementation can scale by module class while maintaining compatible identity, safety, and data semantics.

## Required validation

- ultimate/proof load cases derived from system analysis;
- fatigue/cycle requirements;
- lock/unlock cycle testing;
- false-lock and partial-engagement detection;
- connector mating durability;
- power fault and isolation tests;
- release behavior under defined load states;
- inspection/maintenance criteria.
