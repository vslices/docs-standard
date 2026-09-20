# Validity, degradation, and obsolescence

## Research question

> Is validity and degradation a responsibility owned independently by each Document, a reusable semantic dimension across Documents, or a distinct documentary responsibility?

## Observation

Multiple Document reviews independently produced questions about when preserved knowledge stops representing reality correctly.

This is different from artifact maintenance.

The concern is not primarily:

> When should this file be edited?

It is:

> Under what conditions does the knowledge represented here stop being trustworthy, applicable, or representative?

## Evidence accumulated

### Context

- What would change if an assumption were false?
- What conditions would make this context obsolete?
- What signals would indicate that it stopped being representative?

Validity here concerns whether the context still represents the environment in which the target is interpreted.

### Structure

- When does this structure stop representing the target correctly?
- What changes would invalidate parts of the model?
- What relations could change?
- What parts could appear or disappear?
- What signals indicate that the structure is outdated?

Validity here concerns drift between represented organization and actual organization.

### Domain Vocabulary

- When does this vocabulary stop representing the shared language correctly?
- What terms stopped corresponding to the domain?
- What meanings changed?
- What new concepts appeared?
- What distinctions stopped being useful?
- What signals indicate that the vocabulary is outdated?

Validity here concerns drift between documented language and language actually needed to communicate with precision.

### Decision Record

- What would make this decision need review?
- What assumption would have to change?
- What new evidence could challenge it?
- What contextual change could invalidate it?
- What unexpected consequence could justify reopening it?
- What signals indicate that its foundations no longer hold?

Decision Record adds an important nuance: validity may be intrinsic to the semantics of a decision because a reconstructible decision should preserve the conditions under which its rationale remains defensible.

## Accumulated validity vocabulary

Recurring patterns include:

- false assumption;
- model invalidation;
- loss of representativeness;
- obsolescence;
- drift;
- meaning change;
- new concepts appearing;
- distinctions losing usefulness;
- foundations no longer holding;
- contextual change;
- contradictory new evidence.

## Emerging hypothesis

The evidence currently supports at least three possible models:

~~~text
A. validity belongs independently to each Document

B. validity is a transversal semantic dimension
   specialized by each Document

C. validity is represented by a separate Document
   that references other Documents
~~~

Current evidence from Decision Record makes model B particularly interesting, but this is not yet a conclusion.

## Distinction from maintenance

~~~text
maintenance
    = artifact lifecycle / editing activity

validity
    = whether represented knowledge still holds

degradation
    = process by which representation loses correspondence

obsolescence
    = state where the representation is no longer sufficiently useful or correct
~~~

These distinctions are provisional but useful for keeping implementation concerns separate from knowledge validity.

## Open questions

- Can validity questions share a common vocabulary while retaining Document-specific semantics?
- Does every Document need an explicit validity branch?
- Is degradation always observable through signals?
- Can validity depend on evidence owned by another Document?
- Should a future Nexus connect an assertion with evidence that keeps it valid?
- How should supersession differ from ordinary obsolescence?
- Can knowledge remain historically valid while no longer being currently applicable?

## Current status

Open research pin.

Continue collecting evidence from additional Document types before creating a new Document responsibility.
