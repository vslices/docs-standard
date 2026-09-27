# Diagrams

## Status

Candidate.

This family explores visual notations that help make documentary knowledge, work, relationships, trajectories, composition, and realization easier to inspect.

Diagram definitions are not currently registered in `manifest.yaml`.

Their semantics should continue to emerge through real use before promotion.

## Responsibility

VSlices Docs Standard diagrams **show**.

They do not replace the artifacts that explain, support, compose, connect, or organize knowledge.

Current responsibility boundary:

```text
Documents
    -> explain

Support Notes
    -> support / record

Nexus
    -> compose

Continuity Paths
    -> connect and orient continuity

Diagrams
    -> show
```

A diagram may make work or realization visible while the authoritative explanation remains elsewhere.

## Initial notation family

The first candidate notation is:

- [Action Flow](action-flow.md)

Action Flow represents ordered work through actions and relationships between actions.

It has two principal projections:

```text
Abstract Action Flow
    -> represents work without committing to a system realization

Systematized Action Flow
    -> represents how work is, or is proposed to be, realized by actors and system responsibilities
```

These projections are related but neither replaces the other.

## Design direction

The long-term objective may become a VSlices-oriented visual notation family comparable in role to UML, but specialized for VSlices needs.

That does **not** mean reproducing UML diagram-for-diagram.

The notation should emerge from demonstrated VSlices pressures such as:

- understanding work before implementation;
- connecting work organization with software realization;
- distinguishing semantic responsibility from physical implementation;
- preserving traceability between abstract actions and system actions;
- representing continuity without duplicating documentary sources of truth;
- supporting progressive design from business understanding to implementation.

The notation family should remain small until real cases require additional diagram types.

## Representation technology

Mermaid may be used as an initial rendering mechanism.

Mermaid is not the semantic authority of the notation.

A future Tooling or Surreal Atlas representation may render the same semantics differently.

## Extension

When a new diagram type is proposed:

```text
real representational pressure
-> identify what must be shown
-> verify that another artifact family does not already own the meaning
-> define the smallest useful visual semantics
-> test against real cases
-> preserve unresolved questions
-> promote only after repeated useful application
```

Do not add a diagram type for visual completeness.
