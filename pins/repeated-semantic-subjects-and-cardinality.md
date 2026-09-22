# Repeated semantic subjects and cardinality

## Research question

> Does Docs Standard need to model repeated semantic subjects inside a Document, in addition to questions and answers?

## Observation

The current progressive Document model is naturally expressed as:

~~~text
question
    -> answer
~~~

However, multiple Document types now produce a stronger pattern:

~~~text
one semantic question
    -> N semantic subjects
        -> the same subordinate questions for each subject
~~~

This is not a visual-table concern and should not be reduced to Markdown repetition.

It affects semantic identity, progressive authoring, references, and the shape of the question graph itself.

## Evidence accumulated

### Domain Vocabulary

A Domain Vocabulary contains N terms. Each term may answer the same subordinate questions.

~~~text
¿Qué términos usamos?
├─ Workflow
│  ├─ ¿Qué significa este término?
│  ├─ ¿Dónde aplica?
│  └─ ¿Cómo se relaciona con otros?
└─ Flow
   ├─ ¿Qué significa este término?
   ├─ ¿Dónde aplica?
   └─ ¿Cómo se relaciona con otros?
~~~

The term behaves like a semantic subject internal to the Document.

### Consistency

A Consistency Document may describe one consistency unit containing N consistency rules or invariants.

~~~text
¿Qué reglas sostienen esta consistencia?
├─ Regla A
│  ├─ ¿Qué protege?
│  ├─ ¿Cuándo aplica?
│  ├─ ¿De qué otras reglas depende?
│  └─ ¿Puede evaluarse independientemente?
├─ Regla B
│  └─ ...
└─ Regla C
   └─ ...
~~~

This independently reproduces the Domain Vocabulary problem and promotes it from a local modeling concern to a transversal Docs Standard concern.

### Associated properties in Domain Vocabulary

Domain Vocabulary review added a nested repeated-subject shape:

~~~text
one term
    -> N associated properties
        -> name
        -> definition
        -> requirement / obligatoriness
~~~

This means repeated semantic subjects may be recursive:

~~~text
Vocabulary
    -> N terms
        -> N associated properties per term
~~~

This strengthens the need to distinguish semantic subject identity from question identity and answer cardinality.

### Update

Update provides a third witness with a different shape:

~~~text
one Update
    -> N patch operations
        -> each identifies an answer target
        -> each may expose the same subordinate patch questions
~~~

This suggests repeated semantic subjects may include not only domain subjects such as terms or consistency rules, but transition subjects such as patch operations.

However, an Update patch operation references an existing answer rather than necessarily introducing a new domain subject. That difference must be preserved.

Update also adds another cardinality dimension:

~~~text
1 semantic Update
    -> N patch operations
    -> across M Documents
~~~

The grouping boundary is semantic rather than file-based: multiple answer changes may belong to one Update because together they express one coherent transition.

This should not be confused with technical transactionality.

## Important distinctions

~~~text
question cardinality
    = how many semantic subjects a question may introduce

subject cardinality
    = how many subjects exist under that question

answer cardinality
    = how many answers or relations may exist for one subject and question
~~~

These should not be conflated.

## Semantic subject hypothesis

A repeated item may need stable semantic identity without becoming an independent top-level artifact.

Current strong witnesses:

- a term inside Domain Vocabulary;
- a consistency rule inside Consistency.

Possible future witnesses that still need evidence:

- an alternative inside Decision Record;
- a participant, variation, or subbehavior inside Behavior.

Do not assume names such as collection, entity, record, item, row, or node yet.

## Progressive authoring pressure

- How is a new semantic subject introduced?
- Do subordinate questions become available independently for each subject?
- How does Tooling select subject plus question when the same question identity repeats?
- Can subjects progress through the question graph independently?
- Can one subject reference another subject inside the same Document?
- Can subjects be added after other subjects are already deeply materialized?
- Can an internal subject later become an independent target or Nexus without losing continuity?

## Relationship with Documentary Nexus

Repeated semantic subjects and Nexus granularity may eventually meet, but they should not be conflated prematurely.

A semantic subject may remain internal to one Document.

A Nexus represents a target around which multiple documentary perspectives may compose.

Open question:

> At what point does an internal semantic subject deserve independent target identity and its own Nexus?

## Current status

Open transversal research pin.

Evidence from Domain Vocabulary and Consistency is sufficient to promote this from a Document-local concern.

Do not change the machine-consumable YAML model until subjects, repeated questions, and repeated answers are semantically distinguishable.