# Nexus definitions

This directory specifies the current YAML language for Nexus definitions.

A Nexus composes documentary perspectives around one target. It does not replace the Documents or other Nexus artifacts that may participate in a concrete representation.

The current distinction is:

~~~text
Document
    -> interrogates one target through one documentary responsibility

Nexus
    -> composes perspectives around one target
    -> may ask open questions that specialize that composition

Continuity Path
    -> interrogates and navigates a continuity
~~~

## YAML shape

~~~yaml
kind: vslices-nexus-definition
version: 0.1

nexus:
  type: capability

  scopes:
    - capability

  questions:
    - id: perspective
      text: ¿Qué perspectiva necesita esta composición?
      default: general

  recommendations:
    - document: behavior
      role: Explica qué debe ocurrir al ejercer la capacidad
~~~

Only `kind`, `version`, and `nexus.type` identify the definition language and Nexus type.

`scopes`, `questions`, and `recommendations` are optional unless evidence for a particular Nexus definition requires them.

## `nexus.type`

Stable identity of the Nexus definition.

Tooling should resolve Nexus semantics through this identity rather than through filenames or rendered titles.

## `nexus.scopes`

Declares target kinds for which the Nexus definition is known to be useful.

It is guidance owned by the Nexus type. It is not a claim that every target of that scope requires a Nexus.

## Open questions

A Nexus may declare open questions that help specialize or contextualize the composition.

~~~yaml
questions:
  - id: perspective
    text: ¿Qué perspectiva necesita esta composición?
~~~

Questions are optional. A Nexus does not need a question in order to exist.

Unlike Document questions, Nexus questions must not absorb documentary responsibilities already owned by Documents.

For example, a Capability Nexus should not redefine Behavior by asking `¿Qué debe ocurrir?`.

A Nexus question should instead clarify the composition itself.

### Question identity

Each question has a stable `id` and human-readable `text`.

Question wording may evolve without changing stable identity when its semantic responsibility remains the same.

### Optional default

An open question may provide a default value:

~~~yaml
questions:
  - id: perspective
    text: ¿Qué perspectiva necesita esta composición?
    default: general
~~~

The default is an authoring suggestion, not immutable semantics.

Authors may replace it when the concrete Nexus requires a more specific value.

A default must not be used to turn a Nexus question into hidden Document vocabulary.

## Recommendations

A Nexus may recommend known Docs Standard perspectives that are commonly useful in its composition.

~~~yaml
recommendations:
  - document: behavior
    role: Explica el comportamiento esperado de la capacidad

  - nexus: service-consumption
    role: Organiza la perspectiva de consumo cuando la capacidad se expone como servicio
~~~

A recommendation entry currently references exactly one known definition family:

~~~text
document: <document-type>
or
nexus: <nexus-type>
~~~

### `role`

`role` is the human-readable explanation of what the recommended perspective contributes to this kind of Nexus.

It is not artifact identity, scope, persisted relation identity, or content copied into the recommended artifact.

## Recommendations are open-world guidance

Recommendations describe how Docs Standard knows how to support the composition.

They do **not** define the complete set of artifacts, references, representations, or knowledge that may participate in a concrete Nexus instance.

~~~text
recommendations
    = known guidance

recommendations
    != allowed associations
    != completeness requirement
~~~

A concrete Nexus may associate knowledge or representations that are not present in `recommendations`.

Those concrete associations belong to the representation or instance, not to this definition vocabulary.

For that reason the definition language does not include an `artifact`, `other`, or catch-all recommendation kind.

## Recommendations are not requirements

A recommendation does not imply documentary debt.

Creating a Nexus must not automatically create every recommended Document or Nexus.

Tooling may offer recommendations as authoring actions, but the author chooses which perspectives are useful for the concrete target.

## Semantic coherence

### Nexus composes; Documents explain

Do not duplicate Document questions or content inside a Nexus definition.

### Questions specialize composition

Nexus questions may contextualize composition but must not replace the responsibilities of the artifacts being composed.

### Recommendations point to known standard vocabulary

A `document` value should resolve to a known Document definition.

A `nexus` value should resolve to a known Nexus definition.

The fact that a Nexus definition itself is still experimental or not manifest-registered does not turn its recommendation into a whitelist or requirement.

### Scope presets remain deferred

A future recommendation may help preset generated artifact metadata such as Document scope.

That behavior is not part of the current language.

Document instance scope still needs an explicit promoted semantic contract before Nexus definitions can prescribe such defaults.

### Nexus is distinct from navigation

A Nexus composes perspectives. A Navigation Document explains how to traverse a collection.

### Nexus is distinct from Continuity Paths

A Nexus composes perspectives around a target.

A Continuity Path interrogates and navigates continuity through related points.

A Continuity Path may recommend a Nexus when composition is useful at a point in that trajectory.

## Creating a new Nexus definition

Start from a real target that repeatedly benefits from several documentary perspectives.

Ask:

~~~text
What target is being composed?
Which existing Document or Nexus perspectives repeatedly help?
What does each perspective contribute?
Are open composition questions repeatedly needed?
Would one Document already be sufficient?
Does the composition reduce fragmentation?
~~~

Create the smallest definition that preserves the demonstrated semantics.

Do not add recommendations or questions for symmetrical completeness.

Definitions do not need to be registered in `manifest.yaml` merely because they are being explored. Registration is a separate promotion decision.

## Extending an existing Nexus definition

Extend from real use.

Useful evidence includes:

- the same missing perspective repeatedly appears in concrete Nexus instances;
- the same composition question repeatedly needs to be answered;
- readers repeatedly need the same perspective to understand the target;
- another artifact is absorbing knowledge only because the Nexus cannot currently orient the composition.

Before promoting an addition, ask whether it changes the Nexus vocabulary or merely belongs to one concrete representation.

## Conservative extension loop

~~~text
use the Nexus in a real case
-> observe a recurring composition gap
-> identify whether it is an open question or a known perspective
-> verify that the responsibility belongs to Nexus
-> test it in another case
-> promote only the smallest useful addition
-> use the Nexus again
~~~

## Current candidate definitions

- [Capability Nexus](capability-nexus.yml)
- [Service Consumption Nexus](service-consumption-nexus.yml)

They are evidence-backed candidate definitions, but are intentionally not registered in `manifest.yaml` yet.

Their content should evolve from use.
