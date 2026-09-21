# Realization and the separation between semantics, constraints, decisions, and materialization

## Research question

> Do we need a distinct documentary responsibility for describing how semantics are concretely realized, whether currently or prospectively?

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

> How is this consistency realized?

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

## Declarative, prescriptive, justificatory, and descriptive separation

Subsequent review refined the surrounding responsibilities:

~~~text
Declarative
    = what must be true / what must occur

Prescriptive
    = what constraints and considerations shape acceptable realizations

Justificatory
    = what option was chosen and why

Descriptive
    = what concrete realization exists or is intended
~~~

Current mapping:

~~~text
Behavior / Consistency
    -> declarative

Constraint
    -> prescriptive

Decision Record
    -> justificatory

Realization
    -> descriptive
~~~

Realization should not own the question:

> What should be considered when choosing a realization?

That belongs primarily to Constraint.

Nor should it own:

> Which option should we choose?

That belongs to Decision Record.

Realization describes a concrete realization.

## One responsibility, multiple realization states

A key refinement is that current and proposed realization do not require different Document types.

They answer the same semantic responsibility at different positions relative to materialization.

The root question can therefore remain atemporal:

> How is it realized?

and a realization may be interpreted as:

~~~text
current / observed
    -> How is it realized now?

proposed / intended
    -> How will it be realized?
~~~

This does not make proposed Realization prescriptive.

A proposed Realization is a prospective description of a concrete target state.

It says:

> this is the realization we intend to materialize.

It does not say:

> every acceptable realization must look like this.

That distinction belongs to Constraint.

## Important distinction: prescriptive vs prospective descriptive

~~~text
Constraint
    -> shapes the option space

Realization (proposed)
    -> describes one concrete intended state inside that option space
~~~

For example:

~~~text
Constraint:
    The system must tolerate multi-region deployment.

Decision:
    Choose regional authority with asynchronous reconciliation.

Realization (proposed):
    Inventory ownership will be partitioned by region,
    with reconciliation through asynchronous messages.
~~~

The third statement is still descriptive, but prospective.

## Current and proposed must not be silently mixed

A single representation must not blur:

~~~text
what exists now
+
what is intended later
~~~

Otherwise documentary continuity becomes ambiguous.

A sentence such as:

> The application uses Kafka.

must not mean:

> The application currently does not use Kafka, but we plan to.

The same Document type may represent current and proposed realization, but the state of each realization must remain semantically distinguishable.

How that distinction is encoded is a later modeling/tooling question.

## Relationship with Structure

Structure may describe concrete organization.

Open question:

> When does describing implementation structure remain Structure, and when does it become Realization?

Potential distinction:

~~~text
Structure
    = how parts are organized and related

Realization
    = which concrete mechanisms embody previously defined semantics
~~~

A Realization may reference structural knowledge rather than duplicate it.

## Relationship with Behavior and Consistency

Behavior and Consistency define expected semantics:

~~~text
Behavior
    -> What must occur?

Consistency
    -> What must remain coherent?
~~~

Realization describes how those semantics are embodied:

~~~text
Realization
    -> How is that behavior / consistency realized?
~~~

Changing the realization should not necessarily change the originating declarative semantics.

## Relationship with Constraint

Constraint defines pressures and restrictions on possible realizations:

~~~text
Constraint
    -> What conditions the realization space?
~~~

Realization references or responds to those constraints by describing a concrete state.

Constraint does not itself select or describe the chosen mechanism.

## Relationship with Decision Record

Decision Record records why a realization direction was selected:

~~~text
Decision
    = why this option was selected

Realization
    = what concrete state embodies that selection
~~~

A Decision may justify a proposed Realization.

A Realization should not need to repeat the full rationale.

## Relationship with Update

The new evidence strongly suggests:

~~~text
Realization
    = state

Update
    = transition
~~~

A proposed Realization describes a target state.

An Update describes the transformation intended to move from one realization state to another.

After execution, Update can preserve what was actually changed and what was not.

The resulting current Realization should then be updated to describe what actually exists.

This relationship is tracked in:

- [Realization and Update continuity](realization-update-continuity.md)

## Relationship with Drift

A Realization can participate in at least two comparisons:

~~~text
documented current realization
vs
observed implementation
    -> possible realization drift
~~~

and:

~~~text
proposed realization
vs
resulting current realization
~~~

However, not every difference is Drift.

If the difference is explicitly explained and reconciled through Decision, Update, and revised Realization, it is evolution.

Drift is a candidate when divergence remains unreconciled.

## Software Project Continuity Path

Realization appears increasingly central to the Software Project Continuity Path.

A provisional path is:

~~~text
Behavior / Consistency
    -> declarative semantics

Constraint
    -> pressures on possible realizations

Decision Record
    -> selected direction and accepted tradeoffs

Realization (proposed)
    -> concrete intended state

Update
    -> intended and observed transition

Realization (current)
    -> concrete resulting state

Verification
    -> evidence that realization preserves expected semantics

Drift
    -> unreconciled divergence
~~~

This is not a waterfall.

New evidence can cause earlier knowledge to be revised.

## Authority distinction

Preserve the VSlices distinction:

~~~text
semantics
authority
mechanism
realization
~~~

That something implements or enforces a rule does not automatically make it the semantic authority for that rule.

A Realization Document should describe realization without silently claiming ownership of the semantics it realizes.

## Candidate root-question space

The responsibility is now clearer.

Strong root candidate:

> ¿Cómo se realiza?

Contextual variants:

~~~text
current
    -> ¿Cómo está realizado?

proposed
    -> ¿Cómo se realizará?
~~~

The root itself should not force temporal state into the Document type.

## Open questions

- Is Realization fully distinct from Structure?
- What minimum knowledge makes a concrete state a Realization rather than merely a Structure?
- Can one Realization satisfy several declarative Documents?
- Can one semantic requirement have several simultaneous Realizations?
- How should Realization reference the semantics it embodies?
- How should Realization reference the Constraints and Decisions that shaped it?
- Can Realization describe non-software mechanisms such as organizational processes?
- How should current and proposed realization states be represented without multiplying Document types?
- Can several proposed realizations coexist before a Decision selects one?
- Does an unselected candidate belong to Realization, another proposal artifact, or only exploratory work?
- When should a proposed Realization become current?
- How does superseded proposed realization remain historically reconstructible?
- How should Realization drift be distinguished from explicit evolution?

## Current status

Open research pin with a strengthened candidate responsibility.

Current evidence favors one Realization Document type with distinguishable current and proposed states.

Preserve:

> what must hold first;
> what constrains the option space second;
> what was chosen third;
> how it is or will be realized fourth.
