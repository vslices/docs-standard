# Realization and the separation between requirement and materialization

## Research question

> Do we need a distinct documentary responsibility for describing how required semantics are actually realized in software or another concrete system?

## Origin

The question became explicit during Consistency review.

Consistency can describe:

~~~text
what must remain coherent
what must remain true
when consistency must hold
who has semantic authority over change
~~~

but a separate question appears naturally:

> How is this consistency actually realized?

Possible realizations include:

- Aggregate Root;
- coordinating service;
- database transaction;
- database constraint;
- lock;
- orchestration;
- message coordination;
- workflow;
- several tables modified through one authority;
- other implementation mechanisms.

The original lesson behind Consistency is precisely that these mechanisms are not the semantics themselves.

~~~text
consistency semantics
!=
consistency realization
~~~

An Aggregate Root is one way to realize a consistency unit. It does not define the semantic ceiling of consistency.

## Broader hypothesis

The same separation may recur beyond Consistency:

~~~text
Behavior
    -> what must occur

Realization
    -> how that behavior is currently implemented

Consistency
    -> what must remain coherent

Realization
    -> what mechanism currently preserves that coherence
~~~

This suggests a broader documentary axis:

~~~text
what must be true / what must happen
vs
how it is concretely realized
~~~

The second side may deserve a distinct Document responsibility. This is not yet a conclusion.

## Candidate root-question space

Possible formulations include:

- ¿Cómo se realiza?
- ¿Cómo está realizado?
- ¿Cómo se materializa?
- ¿Cómo está implementado?

None is selected yet.

An important distinction may exist between current and intended realization:

~~~text
¿Cómo está realizado?
    -> descriptive / observed current state

¿Cómo debería realizarse?
    -> prescriptive design intent
~~~

These may not belong to the same documentary responsibility.

## Relationship with existing Documents

### Structure

Structure may already describe part of the concrete organization.

Open question:

> When does describing implementation structure remain Structure, and when does it become Realization?

Potential distinction:

~~~text
Structure
    = how parts are organized and related

Realization
    = which concrete mechanisms embody previously defined semantics
~~~

### Behavior

Behavior defines expected semantics:

~~~text
¿Qué debe ocurrir?
~~~

Realization may instead describe which code path, component, process, handler, service, or mechanism makes it occur.

Behavior should remain valid even if its realization changes.

### Consistency

Consistency provides the strongest witness:

~~~text
¿Qué debe mantenerse coherente?
    -> semantic requirement

¿Cómo se preserva actualmente?
    -> realization
~~~

Changing Aggregate Root to service orchestration should not necessarily change the Consistency Document if the semantic unit and invariants remain the same.

### Decision Record

A Decision Record may explain why a realization was chosen, but it does not itself describe the complete realization.

~~~text
Decision
    = why this direction was selected

Realization
    = what currently embodies that direction
~~~

## Software Project Continuity Path

This pin is especially relevant to the Software Project Continuity Path.

A software-project path may need to preserve continuity across:

~~~text
domain / product semantics
    -> documentary expectations
    -> design decisions
    -> concrete realization
    -> verification
    -> evolution
~~~

A recurring concern is that VSlices can describe what should be true without yet having a clear documentary responsibility for describing what concrete software currently exists as its realization.

If Realization becomes a Document, Software Project may be able to connect:

~~~text
What must be
    -> references
How it is realized
~~~

rather than forcing expected semantics and implementation details into the same Document.

This separation matters for migration and evolution:

~~~text
expected semantics stay stable
while realization changes
~~~

or:

~~~text
realization stays present
while expected semantics are revised
~~~

Those are materially different changes.

## Authority distinction

The pin must preserve the VSlices distinction between:

~~~text
semantics
authority
mechanism
realization
~~~

That something implements or enforces a rule does not automatically make it the semantic authority for that rule.

A Realization Document, if it exists, should describe realization without silently claiming ownership of the semantics it realizes.

## Descriptive versus prescriptive realization

One major unresolved tension is whether Realization should describe:

1. the system as it currently exists;
2. the realization we intend to build;
3. both, with an explicit distinction.

~~~text
current realization
!=
target realization
~~~

Conflating them would recreate exactly the continuity loss this research is trying to avoid.

This may eventually interact with Drift:

~~~text
intended realization
vs
observed realization
    -> implementation / realization drift
~~~

Do not promote this relation yet.

## Relationship with Documentary Nexus

A Nexus may allow a target to connect several perspectives:

~~~text
Nexus(Target)
├─ Behavior
├─ Consistency
├─ Structure
├─ Decision Record
└─ Realization?
~~~

Realization may therefore be one documentary perspective around the same target rather than the owner of the target itself.

This supports the hypothesis:

> the realization references the requirement rather than redefining it.

For example:

~~~text
Consistency
    defines the consistency requirement

Realization
    references that requirement
    and describes the mechanism that currently enforces it
~~~

## Open questions

- Is Realization actually a new Document type?
- Is it already fully covered by Structure plus other existing Documents?
- Is there one Realization Document or several specialized realization perspectives?
- Should realization be descriptive, prescriptive, or explicitly distinguish both?
- What is the correct root question?
- What does Realization own that Structure does not?
- What does Realization own that Decision Record does not?
- Can one realization satisfy several semantic Documents?
- Can one semantic requirement have several realizations?
- How are alternative realizations represented?
- How does a realization reference the semantic requirement it implements?
- Can Realization describe non-software mechanisms such as organizational processes?
- Does Software Project need Realization as a central continuity step?
- How should realization changes be distinguished from semantic changes?
- Does implementation drift belong to Drift, Realization, or their relation?

## Current status

Open research pin.

Do not add realization questions to Consistency merely because the current implementation mechanism is useful to know.

Preserve the separation:

> what must hold first; how it is realized second.

The second may reference the first without redefining it.