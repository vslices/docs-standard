# Realization and Update continuity

## Research question

> How should Realization and Update cooperate to preserve continuity between current state, intended state, executed change, and resulting state?

## Observation

Realization research produced a useful state / transition distinction:

~~~text
Realization
    = describes a concrete state

Update
    = describes a transition between states
~~~

This appears highly relevant to the Software Project Continuity Path.

## Proposed continuity cycle

A provisional cycle is:

~~~text
Realization (current)
    -> describes what exists now

Constraint
    -> constrains future realization options

Decision Record
    -> records the selected direction

Realization (proposed)
    -> describes the intended target state

Update (planned)
    -> describes the changes intended to move current toward proposed

execution

Update (observed/result)
    -> records what was changed and what was not

Realization (current)
    -> is revised to describe what actually exists
~~~

This is not necessarily one linear workflow.

It describes continuity relationships between documentary responsibilities.

## One Realization type, multiple states

The current hypothesis is:

~~~text
Realization current
    -> state that exists

Realization proposed
    -> state intended to exist
~~~

Both belong to the same documentary responsibility.

The difference is temporal / intentional state, not Document type.

## Update as answer-level transition knowledge

Update review added a crucial refinement:

~~~text
Update
    does not replace whole Documents
    patches specific answers
~~~

A single Update may therefore apply N patch operations across M Documents.

The transition knowledge is answer-level rather than file-level.

This is tracked in:

- [Documentary patch semantics](documentary-patch-semantics.md)

## Update as transition knowledge

Update does not own the target state itself.

It owns change knowledge.

Potential semantic distinction:

~~~text
Realization
    = what the state is

Update
    = what will change / what changed
~~~

A planned Update may therefore reference:

- source current Realization;
- target proposed Realization;
- specific documentary answers that must change to preserve the transition;
- patch operations required to move those answers from their current to intended state.

After execution, an Update may preserve:

- changes completed;
- changes not completed;
- changes performed differently than planned;
- newly discovered work;
- reasons for deviation where known.

The exact Update semantics must be reviewed independently.

## Planned versus observed Update

Update review now provides stronger evidence for treating planned and observed change as compatible but independently representable Update Documents:

~~~text
planned Update
    = what we intend to change

observed Update
    = what actually changed
~~~

There is no need to force both roles into one mutable Update artifact.

Several Updates may participate in reconstructing one evolution:

~~~text
planned Update
-> execution
-> observed Update
-> resulting Realization
~~~

This preserves write-once historical knowledge while allowing actual results to differ from the plan.

Whether Docs Standard eventually names these states or relations remains open.

## Reconciliation after execution

After change occurs, documentary continuity should prefer reality over the original plan.

If:

~~~text
proposed realization
    = A + B + C

actual result
    = A + B + C'
~~~

then the resulting current Realization should describe:

~~~text
A + B + C'
~~~

not preserve C merely because it was planned.

The planned state remains historical evidence.

## Difference between deviation and Drift

A deviation from plan is not automatically Drift.

If the deviation is known and reconciled:

~~~text
plan
    -> C

execution
    -> C'

Update / Decision explains change

Realization updated
    -> C'

=> explicit evolution
~~~

If the divergence remains unexplained or undocumented:

~~~text
plan
    -> C

reality
    -> C'

representation still claims C

=> Drift candidate
~~~

This relationship materially refined the Drift hypothesis.

## Relationship with Decision Record

Update should not silently absorb decision rationale.

If execution changes because a new choice was made, a Decision Record may be required to preserve why.

Provisional distinction:

~~~text
Decision
    = why the direction changed

Update
    = what change was planned / performed

Realization
    = what state results
~~~

## Relationship with Constraint

Constraint can change before or during an Update.

A newly discovered hard or soft constraint may:

- invalidate the proposed Realization;
- force a new Decision;
- alter the Update;
- produce a new proposed Realization.

Do not encode that causal chain as mandatory workflow yet.

## Software Project Continuity Path

This pin is strongly connected to Software Project.

A provisional continuity geometry is:

~~~text
Behavior / Consistency
    -> what must hold

Constraint
    -> what shapes acceptable realization

Decision
    -> what direction is selected

Realization (proposed)
    -> what concrete target state is intended

Update
    -> what transition is planned

execution

Update
    -> what transition actually occurred

Realization (current)
    -> what concrete state now exists

Verification
    -> what evidence shows expected semantics are preserved

Drift
    -> what divergence remains unreconciled
~~~

This should be tested when Software Project Continuity Path is reviewed directly.

## Open questions

- Is Update fundamentally a transition Document?
- Can one Update target several proposed Realizations?
- Can one proposed Realization require several Updates?
- Is a proposed Realization required before an Update can exist?
- Can an Update itself define enough target-state detail without duplicating Realization?
- Should planned and observed Update be named states, relations between separate Updates, or simply inferred from their evidence and role?
- How should partial completion be represented?
- What happens when execution intentionally diverges from the proposed Realization?
- When must a new Decision Record be created?
- When does unfinished work remain Update state versus becoming Drift?
- How are superseded proposed Realizations preserved?
- Can several proposed Realizations coexist as alternatives before Decision?
- Does Realization become current through explicit promotion or simply through observed reality?
- What evidence is required before considering a proposed Realization realized?

## Current status

Open research pin.

Do not promote this cycle into a mandatory workflow.

Use it as evidence when reviewing Update Document and Software Project Continuity Path.
