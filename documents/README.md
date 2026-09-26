# Document definitions

This directory contains the normative Document vocabulary consumed by VSlices Tooling.

The definitions here are not copies of finished Markdown templates. They describe the questions a Document type can use to progressively deepen its answer.

Research material under `vslices/docs/es/alive-lab/research/notes/docs-standard/artifacts` is evidence and design history for this standard. It is not the normative source consumed by Tooling.

## Document model

A Document specializes in one root question.

Additional questions refine that root question through a parent/child cascade. A child question does not establish an independent concern: it adds a more precise perspective to the question above it.

For example, a Context Document may evolve from:

```text
¿Dónde existe?
```

to:

```text
¿Dónde existe?
└─ ¿Qué estamos asumiendo como cierto?
```

A Document does not need to materialize every question defined by its type. Unmaterialized questions are possibilities, not missing work.

## Conservative question extension

A Document definition should grow from evidence produced while using the Document, not from an attempt to make its question tree exhaustive in advance.

A root question may remain the only promoted question until real use exposes a distinction that deserves to be interrogated explicitly.

The current extension discipline was derived from the detailed review of Context, Structure, Domain Vocabulary, Consistency, and Update.

### When a new question deserves consideration

A candidate question should respond to an observed pressure in real use.

Useful evidence includes cases where:

- the current question permits materially different interpretations;
- an answer repeatedly hides an important distinction;
- reviewers repeatedly need to ask the same follow-up question;
- two materially different cases produce answers that look equivalent without further refinement;
- a decision, design, implementation, or validation outcome depends on a distinction that the current graph does not expose;
- a repeated semantic subject needs the same subordinate interrogation;
- an existing question repeatedly absorbs knowledge that belongs to a different documentary responsibility.

The existence of a possible question is not sufficient evidence for promoting it.

### Semantic pressure criterion

A child question deserves to exist when it adds useful semantic pressure to its parent.

A useful child question should make at least one relevant distinction more explicit without becoming an independent documentary responsibility.

Before adding a question, ask:

~~~text
What ambiguity does this reduce?
What distinction does this expose?
Can the answer change understanding, decision, design, implementation, or validation?
Does this genuinely refine the parent question?
Does another existing question already capture the same knowledge?
Would this question be better expressed as a different Document responsibility?
~~~

If these questions do not produce a concrete reason for the child to exist, prefer not to add it yet.

### Prefer observed gaps over symmetrical completeness

Do not add questions merely because a neighboring branch contains an analogous question.

For example:

~~~text
branch A has X
therefore branch B should probably also have X
~~~

is not enough evidence.

Symmetry can be aesthetically attractive while adding no semantic value.

Prefer:

~~~text
real case
-> current question becomes insufficient
-> missing distinction becomes visible
-> candidate question is proposed
-> candidate is tested against another case
-> question is promoted if it continues to add useful pressure
~~~

### Do not confuse depth with quality

A deep question is not automatically excessive.

A shallow question is not automatically fundamental.

Question depth should follow the semantic distinction being investigated.

Do not flatten a useful distinction merely to keep the tree small, and do not deepen a branch merely to make it appear thorough.

### Avoid questions whose answer is already fixed by the Document type

A per-instance question is usually unnecessary when every valid instance must answer it in the same way.

For example, if a property is an invariant of the Document type itself, repeatedly asking each Document instance to confirm that property does not discover new knowledge.

Prefer expressing universal Document semantics as part of the Document definition or its constraints rather than as a question whose answer is predetermined.

### Review closed questions carefully

A question whose natural answer is yes/no deserves extra scrutiny.

Ask whether the useful knowledge is actually the concrete form behind the boolean.

For example:

~~~text
Does X exist?
~~~

may often be stronger as:

~~~text
What X exists?
~~~

with "none" remaining a valid answer.

However, do not reject a closed question solely because it is closed.

A closed answer may provide useful classification while an open question explains the concrete phenomenon. This relationship remains under research and should be evaluated from real cases rather than normalized prematurely.

### Prefer concrete questions over indirect confirmation

Questions should request the knowledge we actually need.

Prefer:

~~~text
What differences exist?
What relationships must be preserved?
What states are acceptable?
~~~

over:

~~~text
Are there differences?
Must relationships be preserved?
Can there be several valid states?
~~~

when the open form captures the relevant semantics directly.

### Merge questions that repeatedly produce the same knowledge

Two differently worded questions should not be preserved merely because they emphasize different wording.

If real answers repeatedly collapse to the same information, consider:

- merging them;
- keeping the stronger question;
- moving a distinction into a subordinate question only if it materially changes interpretation.

Do not merge questions only because they look similar syntactically. The test is whether they discover different knowledge.

### Preserve responsibility boundaries

A question may be useful and still belong to another Document.

Before promoting a child, ask whether it is still refining the same root responsibility.

Examples of distinctions already found useful during review include:

~~~text
Structure
    = how parts are organized

Behavior
    = what must occur

Consistency
    = what must remain coherent

Constraint
    = what conditions possible realizations

Decision Record
    = what was chosen and why

Realization
    = how semantics are concretely realized

Update
    = what semantic transition changes documented answers
~~~

A question should not be retained merely to make one Document self-contained if doing so duplicates another documentary authority.

### Distinguish question cardinality from question proliferation

When the same question applies to several semantic subjects, prefer one question with repeated answer instances over duplicating the question definition.

Typical shape:

~~~text
one question
-> N semantic subjects
   -> same subordinate questions for each subject
~~~

Cardinality exists to represent repeated answers without turning repetition into separate vocabulary.

Do not introduce separate questions solely because there may be several answers.

### Use clear wording for humans and AI

Question wording should minimize accidental interpretation differences.

Prefer wording that:

- names the subject explicitly when pronouns would be ambiguous;
- asks directly for the desired knowledge;
- avoids decorative words that do not change meaning;
- avoids relying unnecessarily on distant parent context;
- distinguishes nearby concepts explicitly;
- remains understandable when read outside a rendered template.

A wording improvement should not silently change the semantic responsibility of the question.

### Keep semantics separate from materialization

Do not add a question because a template, Markdown layout, CLI interaction, persistence format, or rendering mechanism needs a field.

A tooling or presentation need becomes documentary semantics only when it reveals knowledge that the Document itself must preserve.

Likewise, a semantic requirement may constrain Tooling without prescribing the technical mechanism used to realize it.

## Recommended extension loop

For root-only or still-young Documents, use the smallest loop that lets real work pressure the definition:

~~~text
use the Document in a real case
-> answer the currently available questions
-> notice the first place where important meaning cannot be represented clearly
-> identify which existing question owns that gap
-> formulate the smallest question that exposes the missing distinction
-> check whether the question belongs to this Document
-> test it against the real case
-> preserve the observation in a pin if the pattern may be transversal
-> promote the question only when the evidence is sufficient
-> use the Document again
~~~

The objective is not to predict the final question graph.

The objective is to let the graph emerge from repeated semantic pressure while preserving a reconstructible reason for every promoted question.

### Conservative default

When uncertain whether a question should exist:

> Leave it out of the normative YAML until a real case makes its value concrete.

A missing question can be added when evidence appears.

A premature question can silently shape authoring, interpretation, and Tooling before its responsibility is understood.

For young Documents, under-specification is therefore preferable to speculative completeness, as long as observed semantic gaps are preserved as research evidence rather than forgotten.

## Question cardinality

A question may optionally declare:

~~~yaml
cardinality: many
~~~

Cardinality belongs to the question definition and constrains the number of answer instances that one question occurrence may materialize.

The current vocabulary is intentionally minimal:

~~~text
cardinality omitted
    -> one
    -> zero or one materialized AnswerInstance during progressive authoring

cardinality: many
    -> many
    -> zero or more materialized AnswerInstances during progressive authoring
~~~

Children are scoped through an answer instance rather than globally through the question definition:

~~~text
Question
├─ Answer A
│  └─ child Questions for A
└─ Answer B
   └─ child Questions for B
~~~

Each child question may declare its own cardinality independently. This makes cardinality recursively composable.

Cardinality does not imply completeness. Zero materialized answers can remain a valid progressive state until evidence justifies an answer.

The standard does not yet define min/max bounds, ordering, uniqueness, stable AnswerInstance identity, or a separate semantic-subject primitive. Those remain evidence-driven design pressures.

## Progressive authoring

The current authoring model has these invariants:

1. Creating a Document materializes only its root question.
2. The newly created root question may contain the Tooling placeholder that represents "not answered yet".
3. Before the root is answered, only that root question is writable.
4. Once a question is answered, its immediate child questions become available.
5. A non-root question is materialized only together with a valid answer; it does not need an intermediate placeholder state.
6. A materialized child requires its parent to already be materialized. The active question tree is therefore closed over ancestry.
7. An existing answer may be updated later.
8. Discovery exposes the currently editable questions and the immediate unanswered children that can be materialized next.
9. Questions outside that immediate surface are not directly writable.
10. Questions that have not been materialized are not considered incomplete or document debt.

The numeric question selections shown by an interactive CLI are operational conveniences. Stable question identity belongs to the definition; numeric selections do not belong to persisted document semantics.

## Persisted artifact identity

The current persisted front-matter contract is intentionally minimal:

```yaml
---
artifact:
  kind: document
  type: context
---
```

See [`front-matter.md`](./front-matter.md) for the authority classification that led to this shape and for the fields deliberately deferred from the earlier research proposal.

Question text and the question graph are not copied into front-matter. The Document type resolves that vocabulary through the installed Docs Standard, while materialized question blocks preserve only stable question identity.

## Authority boundary

VSlices Docs Standard owns the document vocabulary: Document types, stable question identities, question text, question relationships, and type-specific constraints.

VSlices Tooling owns the authoring mechanism: loading and validating the installed standard, creating artifacts, detecting the current document state, calculating the valid next surface, applying updates, and materializing the result.

Adding another valid child question to a Document type should therefore be a change to this repository, not a code change in Tooling.
