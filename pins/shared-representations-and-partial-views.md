# Shared representations and partial views

## Research question

> Do we need a way to represent shared knowledge once and allow different Documents to project, filter, or emphasize different parts of it?

## Hypothesis

Different Documents may need to observe the same underlying knowledge from different semantic perspectives.

The working analogy is a layered representation: one underlying representation may exist once, while several Documents expose or emphasize different subsets, relations, or interpretations.

This may eventually relate to a documentary Nexus, but that relationship is not decided.

## Evidence accumulated

### Structure

A shared structural representation may be reused while different Documents emphasize different nodes, relations, boundaries, or paths.

The same underlying structure should not necessarily need to be independently reconstructed in each Document.

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

A Decision Record should be able to identify or project affected knowledge without duplicating the complete representation.

Decision and Feedback also suggest a shared surface:

~~~text
Decision
    preserves expectation

Feedback
    observes later outcome
~~~

Feedback may need to contrast later evidence with the original decision without copying the original decision semantics.

## Distinction under investigation

The important distinction is:

~~~text
creating new knowledge
!=
projecting existing knowledge
!=
emphasizing part of existing knowledge
~~~

A Document may need to do one or more of these without becoming the authority for the underlying shared representation.

## Open questions

- What owns the underlying representation?
- Can several Documents reference the same semantic subject without duplicating it?
- Is a documentary Nexus the correct abstraction, or only one possible composition mechanism?
- How are projections kept consistent when the shared knowledge changes?
- Can a projection add Document-specific interpretation without mutating the shared source?
- How do partial views preserve provenance and authority?
- Should the relationship be semantic, materialization-specific, or both?

## Current status

Open research pin.

Do not introduce layers, views, projections, or Nexus semantics into Document definitions solely to satisfy this hypothesis.
