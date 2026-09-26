# Documentary Nexus proposals

## Research question

> Are recurring groups of Documents around concrete targets evidence for reusable Documentary Nexus compositions?

## Observation

As individual Document responsibilities become clearer, some Documents repeatedly appear together around the same target.

This suggests that Nexus research should not only study shared representations and recursive composition, but also recurring documentary constellations.

These constellations are not templates yet.

They are candidate compositions discovered from real continuity needs.

## Working idea

A Documentary Nexus may organize several Documents that describe different semantic perspectives of one target.

~~~text
Nexus(Target)
    -> multiple Documents
    -> each preserves its own root question and authority
~~~

The Nexus does not flatten those Documents into one artifact.

It may make their relationships explicit.

## Emerging software-target constellation

Current research suggests a particularly strong group for software-oriented targets:

~~~text
Nexus(Target)
├─ Behavior
│  -> What must occur?
├─ Consistency
│  -> What must remain coherent?
├─ Constraint
│  -> What constrains possible realizations?
├─ Decision Record
│  -> What was decided?
├─ Realization
│  -> How is it realized?
│     ├─ current
│     └─ proposed
├─ Update?
│  -> What transition is planned or occurred?
└─ Drift?
   -> What divergence remains unreconciled?
~~~

This constellation is strongly related to the Software Project Continuity Path.

## Feeding relationships inside the constellation

Some Documents appear to provide knowledge that supports answers in others.

Examples:

~~~text
Behavior / Consistency
    -> define declarative expectations

Constraint
    -> defines pressures and limits on possible realizations

Constraint
    -> informs
Decision Record

Decision Record
    -> explains why a realization direction was selected

Realization (proposed)
    -> describes the intended concrete target state

Update
    -> may describe the transition toward that state

Realization (current)
    -> describes the concrete state that actually exists

Drift
    -> may capture divergence that remains unreconciled
~~~

These are candidate semantic relationships, not a finalized Nexus schema.

## Declarative, prescriptive, descriptive axis

The emerging constellation also reveals a useful axis:

~~~text
Declarative
    -> what must be true / what must happen

Prescriptive
    -> what conditions and constraints must be considered

Descriptive
    -> how the target is or will be concretely realized
~~~

Current candidate mapping:

~~~text
Behavior / Consistency
    -> declarative

Constraint
    -> prescriptive

Realization
    -> descriptive, current or prospective

Decision Record
    -> connective / justificatory

Update
    -> transitional
~~~

Decision Record does not fit cleanly into only one axis because it records the choice that bridges constraints and realization.

## Target-oriented compositions

Different targets may need different document constellations.

Examples to investigate:

### Software component or service

~~~text
Behavior
Consistency
Constraint
Decision Record
Realization
Update?
Structure
Drift?
~~~

### Business process or workflow

~~~text
Context
Structure
Behavior
Consistency
Constraint?
Decision Record?
Drift?
~~~

### Domain concept

~~~text
Domain Vocabulary
Context
Consistency?
Decision Record?
~~~

The purpose is not to force all Documents onto every target.

The goal is to discover recurring useful compositions.

## Recursive composition

A target Nexus may reference more granular Nexus artifacts:

~~~text
Product Nexus
└─ Service Nexus
   └─ Component Nexus
~~~

Each level may have its own relevant Document constellation.

This supports semantic granularity without embedding every detail into one Document.

## Relationship with Continuity Paths

A Nexus composition and a Continuity Path are related but not necessarily the same thing.

Provisional distinction:

~~~text
Nexus
    = organizes perspectives around a target

Continuity Path
    = organizes how knowledge is discovered, transformed, connected, and evolved through work
~~~

The Software Project Continuity Path may traverse or create several Documents inside one or more Nexus artifacts.

A newly observed candidate continuity chain is:

~~~text
declarative semantics
-> constraints
-> decision
-> proposed realization
-> update
-> current realization
-> verification
-> unreconciled drift
~~~

This is not yet a mandatory sequence or workflow.

## Open questions

- Are Nexus compositions reusable patterns or always target-specific?
- Should Docs Standard define named Nexus kinds?
- Can a Nexus recommend Documents without requiring them?
- Does a Nexus own relations such as Constraint -> informs -> Decision?
- Can one Document participate in several Nexus artifacts?
- Can Nexus composition depend on target kind?
- How should recursive Nexus composition interact with semantic subject promotion?
- What is the minimum semantic content of a Nexus beyond its target identity and relationships?
- Does a Nexus need its own questions?
- How do Nexus proposals differ from Continuity Paths?
- Should Software Project eventually define a canonical or recommended Nexus constellation?

## Current status

Open research pin.

Do not promote these constellations into mandatory templates.

Use recurring target-oriented groupings as evidence for future Nexus semantics.

## Initial normative promotion

Two evidence-backed constellations have now been promoted as minimal Nexus definitions:

- Capability;
- Service Consumption.

Promotion is intentionally smaller than the historical compositions.

Each promoted Nexus currently owns only:

~~~text
type
scopes
recommended Document perspectives
human-readable role per recommendation
~~~

The recommendations remain optional.

The larger software-target constellations, recursive Nexus composition, Nexus-to-Nexus relations, ordering, and other candidate relationships in this pin remain open research.
