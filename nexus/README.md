# Nexus definitions

This directory contains the normative Nexus vocabulary consumed by VSlices Tooling.

A Nexus does not answer a new documentary question. It composes existing documentary perspectives around one target.

The current distinction is:

~~~text
Document
    -> interrogates one target through one documentary responsibility
    -> owns questions and answers

Nexus
    -> composes documentary perspectives around one target
    -> owns composition and recommendation semantics
~~~

A Nexus definition is therefore not a template for a monolithic document.

It describes which Document perspectives are useful for a kind of target and explains what each perspective contributes.

## YAML shape

The current Nexus definition language is intentionally small:

~~~yaml
kind: vslices-nexus-definition
version: 0.1

nexus:
  type: capability

  scopes:
    - capability

  recommendations:
    - document: scope
      role: Defines the boundaries of the capability
~~~

### `kind`

Identifies the definition family.

For definitions in this directory it must currently be:

~~~yaml
kind: vslices-nexus-definition
~~~

### `version`

Identifies the current definition-language version.

The first promoted version is:

~~~yaml
version: 0.1
~~~

This version belongs to the Nexus definition language, not to a generated Nexus artifact instance.

### `nexus.type`

Stable identity of the Nexus type.

Examples currently promoted:

~~~text
capability
service-consumption
~~~

Tooling should resolve Nexus semantics through this identity rather than through filenames or visible titles.

### `nexus.scopes`

Declares the target kinds for which this Nexus type is currently admitted.

This is type-owned vocabulary.

It does not mean that every target of that kind requires a Nexus.

A Nexus should only be created when composition adds useful continuity.

### `nexus.recommendations`

Declares Document perspectives that are commonly useful for this Nexus type.

A recommendation is not a requirement.

The presence of a recommendation must not cause Tooling to create the corresponding Document automatically.

A Nexus instance may begin with none, some, or all recommended perspectives depending on the real target.

### `nexus.recommendations[].document`

References a Document type registered in the installed Docs Standard.

Example:

~~~yaml
document: behavior
~~~

The Nexus does not copy the Document root question or its question graph.

Tooling resolves that vocabulary through the corresponding Document definition.

This preserves one source of truth:

~~~text
Document definition
    -> owns the questions

Nexus definition
    -> references the Document type
~~~

### `nexus.recommendations[].role`

Human-readable explanation of what that Document perspective contributes to this kind of Nexus.

Example:

~~~yaml
- document: behavior
  role: Explains the expected behavior of the capability
~~~

`role` is explanatory vocabulary.

It is not Document identity, artifact scope, persisted relation identity, or an instruction to duplicate the role into generated Document content.

Its purpose is to help humans, AI, and Tooling explain why a recommended perspective may be useful.

## Semantic coherence rules

A Nexus definition should satisfy the following rules.

### Nexus composes; Documents explain

Do not move knowledge owned by a Document into the Nexus definition.

Bad:

~~~yaml
- document: behavior
  question: What must occur?
  expected: ...
~~~

The Behavior definition already owns that question.

Prefer:

~~~yaml
- document: behavior
  role: Explains what must occur
~~~

### Recommendations are optional

A recommendation describes useful composition, not documentary debt.

~~~text
recommended
!=
required
~~~

Tooling should be able to show recommended perspectives without treating missing Documents as incomplete work.

### A Nexus must not create Documents by implication

Creating a Nexus does not mean creating every recommended Document.

A user or authoring workflow may later choose a recommendation and create or attach the corresponding Document.

That transition belongs to Tooling.

### Recommendations reference promoted Document types

A `document` value should resolve to a Document definition registered by `manifest.yaml`.

Do not encode free-form pseudo-Document types inside Nexus definitions.

If a missing documentary responsibility is discovered, first determine whether it deserves a real Document type.

### The target is shared by the composition

A Nexus exists around one semantic target.

The concrete persistence model for Nexus instances is still intentionally small and should be promoted from real authoring evidence.

In particular, `artifact.target` and `artifact.scope` are not introduced here as required persisted Nexus-instance fields merely because historical artifacts used them.

### Scope presets are not yet normative

Research suggests that a Nexus recommendation may eventually help preset Document-instance metadata such as `scope`.

That is not part of the current Nexus definition language.

Document `artifact.scope` is still deferred in the current persisted artifact model.

Do not introduce recommendation-level scope defaults until Document instance scope has a demonstrated and promoted semantic contract.

### Composition is distinct from navigation

A Nexus explains which documentary perspectives compose around a target.

A Navigation Document explains how a human should traverse a collection or route.

A Nexus may later support suggested reading order, but reading order is not part of the current minimum normative language.

### Composition is distinct from Continuity Paths

A Nexus composes perspectives around a target.

A Continuity Path is expected to preserve how knowledge connects or evolves across work and perspectives.

Do not encode Continuity Path semantics in Nexus definitions merely because a Nexus participates in such a path.

## Creating a new Nexus type

Prefer the smallest evidence-supported definition.

Start from a real target that repeatedly needs several Document perspectives.

Ask:

~~~text
What target kind is being composed?
Which existing Document perspectives are repeatedly useful?
What does each perspective contribute?
Would one Document already be sufficient?
Does the composition reduce fragmentation?
~~~

If one Document already preserves enough intent, do not create a Nexus.

If composition is useful, create a new definition with:

1. a stable `nexus.type`;
2. the smallest demonstrated `scopes` set;
3. only the Document recommendations supported by real evidence;
4. a human-readable `role` for each recommendation;
5. registration in `manifest.yaml`.

Do not add recommendations merely to make the Nexus look complete.

## Extending an existing Nexus type

Extend a Nexus when real use shows that the current composition repeatedly omits a useful documentary perspective.

Useful evidence includes:

- authors repeatedly create the same additional Document type around this Nexus target;
- readers repeatedly need the same missing perspective to understand the target;
- the same Document type consistently plays a recognizable role in several instances;
- omitting the perspective causes fragmentation or forces another Document to absorb a foreign responsibility.

Before adding a recommendation, ask:

~~~text
Does this Document type already exist?
Does it answer a distinct documentary responsibility?
Is it useful specifically in this Nexus composition?
Can its role be explained without duplicating its content?
Is the pattern repeated enough to promote?
~~~

When uncertain, keep the observation in research rather than promoting the recommendation.

## Conservative extension loop

~~~text
use a Nexus in a real case
-> compose the Documents that are actually needed
-> observe the first recurring missing perspective
-> verify that an existing Document owns that perspective
-> describe why it contributes to this Nexus type
-> test the recommendation in another real case
-> promote it only when the pattern remains useful
-> use the Nexus again
~~~

The objective is not to define a universal matrix of Documents by target type.

The objective is to preserve useful, evidence-backed composition.

## Current promoted Nexus types

- [Capability Nexus](capability-nexus.yml)
- [Service Consumption Nexus](service-consumption-nexus.yml)

These are initial executable witnesses.

They should be extended from real authoring evidence rather than from the larger historical compositions in `vslices/docs`.
