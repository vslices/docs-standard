# Documentary Nexus, shared representations, and semantic granularity

## Research question

> How should multiple documentary perspectives compose around the same target without duplicating knowledge, while allowing the target to be decomposed recursively into more granular targets?

## Emerging hypothesis

A Document and a Nexus appear to have different semantic centers:

~~~text
Document
    = interrogates a target through one root question

Documentary Nexus
    = composes multiple documentary perspectives around the target itself
~~~

A Document asks one kind of question about a target.

A Nexus may instead provide the composition surface through which several Documents about that same target are discovered, related, or navigated.

This remains a hypothesis. It is not normative Nexus semantics yet.

## Shared representations and partial views

Different Documents may need to observe the same underlying knowledge from different semantic perspectives.

The working analogy is a layered representation:

~~~text
one underlying representation
    -> multiple documentary views
        -> each emphasizes a different semantic dimension
~~~

The important distinction is:

~~~text
creating new knowledge
!=
projecting existing knowledge
!=
emphasizing part of existing knowledge
~~~

A Document may project or emphasize knowledge without becoming the authority for the underlying representation.

### Structure and Behavior

Behavior produced the clearest witness so far.

The same flow may support at least two distinct perspectives:

~~~text
same flow

Structure
    -> how it is organized
    -> nodes, containment, ordering, relations

Behavior
    -> what occurs while traversing it
    -> transformations, decisions, outcomes, effects
~~~

Neither perspective should necessarily need to recreate the whole representation independently.

### Domain Vocabulary

Relations between terms can form a semantic graph:

- broader / narrower;
- contains / is part of;
- alternative;
- complementary;
- depends on a distinction.

Other Documents may need to reference or emphasize those same concepts without redefining the vocabulary.

### Decision Record

A decision frequently affects knowledge owned elsewhere:

- documented knowledge;
- structures;
- behavior;
- implementation;
- processes;
- other decisions.

A Decision Record should be able to identify or project affected knowledge without duplicating its complete representation.

Decision and Feedback also suggest a shared surface:

~~~text
Decision
    preserves expectation

Feedback
    observes later outcome
~~~

Feedback may need to contrast later evidence with the original decision without copying the decision semantics.

## Semantic granularity

Structure and Behavior both produced questions about the level at which a target is being treated as a unit.

Structure asks questions such as:

- what level are we observing?
- what detail is hidden?
- what internal structure is collapsed inside one represented part?

Behavior asks questions such as:

- what behavior are we treating as one unit?
- what smaller behaviors compose it?
- which parts deserve their own Behavior Document?
- which parts should only be referenced?

This suggests:

~~~text
question depth
!=
target depth
~~~

A deeper question continues interrogating the same target.

A more granular target introduces a different target that may deserve its own documentary perspectives.

## Recursive decomposition

A Nexus may provide a natural recursive composition model.

Example:

~~~text
Work Line Nexus
├─ Context Document
├─ Structure Document
├─ Behavior Document
│
├─ Process Nexus A
│  ├─ Behavior Document
│  └─ Structure Document
│
└─ Process Nexus B
   ├─ Behavior Document
   └─ Workflow Nexus
      ├─ Behavior Document
      └─ Structure Document
~~~

The working hypothesis is:

> A Nexus may contain or relate Documents about its target and may recursively contain or relate Nexus artifacts for more granular targets.

This should not yet be read as a final containment model.

## Composition principle under investigation

A useful provisional formulation is:

> Documents interrogate knowledge. Nexus artifacts compose knowledge.

This formulation helps distinguish semantic questioning from documentary composition, but it remains revisable.

## Emerging document constellations

Research has now produced recurring groups of Documents around concrete targets.

The detailed candidate constellations are tracked separately in:

- [Documentary Nexus proposals](documentary-nexus-proposals.md)

The important connection to this pin is that recursive Nexus composition may organize not only multiple views of shared knowledge, but also recurring semantic roles around a target:

~~~text
declarative
prescriptive
justificatory
descriptive
comparative
~~~

This strengthens the Nexus hypothesis without yet making any constellation mandatory.

## Open questions

- Does a Nexus contain Documents, relate them, or both?
- Can a Nexus contain or reference other Nexus artifacts recursively?
- Does a Nexus need a root question, or is its semantic center the target itself?
- What knowledge, if any, belongs directly to the Nexus?
- Should shared representations live in the Nexus or only be referenced through it?
- Can several Documents reference the same semantic subject without duplicating it?
- Can one representation support multiple semantic projections?
- How are projections kept consistent when the shared knowledge changes?
- Can a projection add Document-specific interpretation without mutating the shared source?
- How do authority and provenance work across projections?
- How do we decide when a nested concept deserves its own Nexus?
- Can a Document refer to a more granular Nexus instead of recursively embedding all its detail?
- How should recursive Nexus composition preserve continuity across levels?

## Current status

Open research pin.

Evidence currently supports treating shared representations, partial views, semantic granularity, recursive decomposition, and the Documentary Nexus hypothesis as one connected research space rather than separate abstractions.

Do not introduce Nexus semantics into Document definitions solely to satisfy this hypothesis.
