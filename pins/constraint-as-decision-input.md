# Constraint as decision input

## Research question

> How should Constraint knowledge feed and justify Decision Record answers without collapsing the two responsibilities into one Document?

## Observation

Constraint and Decision Record answer different questions but are strongly connected.

~~~text
Constraint
    = what conditions, limits, pressures, or considerations shape the space of acceptable realizations

Decision Record
    = what option was selected, why it was selected, and what tradeoffs were accepted
~~~

A Constraint Document does not choose an option.

A Decision Record should not need to rediscover or restate all constraints that informed the choice.

## Working relationship

A useful provisional relation is:

~~~text
Constraint knowledge
    -> feeds / constrains
Decision criteria and alternative evaluation
    -> supports
Decision rationale
~~~

The Constraint Document may justify answers such as:

- why an alternative was not viable;
- why a criterion mattered;
- why one option satisfied the environment better than another;
- why a risk was relevant;
- why a particular tradeoff became necessary.

However, the Decision Record remains the authority for:

- which option was chosen;
- which tradeoff was accepted;
- which risks were consciously accepted by that decision;
- why the choice was made under the available evidence.

## Important distinction

~~~text
Constraint
    identifies pressure or limitation

Decision
    chooses how to respond to that pressure
~~~

Example:

~~~text
Constraint
    Global strong consistency would exceed the accepted latency envelope.

Decision
    Prefer regional authority and accept eventual cross-region convergence.
~~~

The tradeoff belongs to Decision because it exists only once an option is selected.

## Hard and soft constraints

A Constraint Document may distinguish:

~~~text
hard constraint
    -> violating it makes a realization unacceptable

soft constraint
    -> should influence evaluation but may be sacrificed with justification
~~~

This supports the relationship with Decision Record:

~~~text
hard constraints
    -> eliminate options

soft constraints
    -> shape criteria and tradeoffs
~~~

## Risk boundary

Risk should remain contextual to the responsibility that owns it.

~~~text
Constraint risk
    = what may happen if this constraint or consideration is ignored

Decision risk
    = what risk is consciously accepted by choosing this option
~~~

These can reference each other but should not be merged.

## Potential graph relationship

This relationship may later become explicit in Docs Standard or Nexus semantics:

~~~text
Constraint Document
    -> informs
Decision Record
~~~

Possible relation names are intentionally not selected yet.

## Open questions

- Should Decision Record explicitly reference the Constraints that influenced it?
- Should a criterion in Decision Record point to one or more Constraints?
- Can one Constraint influence several decisions?
- Can one decision satisfy some constraints while intentionally violating or relaxing others?
- How should a soft constraint become an accepted tradeoff?
- Should rejected alternatives preserve which constraints made them unacceptable?
- How should historical Decision Records behave when Constraints later change?
- Can Constraint drift trigger decision review without rewriting the original Decision Record?
- Does this relationship belong directly to Document semantics or to a Documentary Nexus?

## Current status

Open research pin.

Preserve the separation:

> Constraint explains what shapes the choice. Decision Record explains the choice that was made.