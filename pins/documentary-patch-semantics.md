# Documentary patch semantics

## Research question

> Should Update be modeled as a reversible semantic patch over answers rather than as replacement of whole Documents?

## Evidence from Update Document review

The historical Update Document was organized around an artifact target and textual segments.

The semantic review produced a stronger model:

~~~text
Update
    does not replace a whole Document

Update
    patches one or more answers
    across one or more Documents
~~~

The closest operational analogy is an HTTP PATCH, but the responsibility is documentary and semantic rather than transport-specific.

## Answer-level target

The primary update target is not necessarily:

- a file;
- a heading;
- a Markdown segment;
- an entire Document.

It is the semantic answer associated with a question in a Document.

A single Update may therefore contain several patch operations:

~~~text
Update
├─ patch answer A in Document X
├─ patch answer B in Document X
├─ patch answer C in Document Y
└─ patch answer D in Document Z
~~~

This means one Update may span several Documents while remaining one coherent change artifact.

## Reversible patch hypothesis

An Update should preserve enough semantic information to reconstruct:

~~~text
before
-> operation
-> after
~~~

without requiring a complete snapshot of the affected Documents.

This may make an Update reversible in the documentary sense.

Possible operations include, provisionally:

- add an answer;
- replace or revise an answer;
- remove an answer;
- possibly change the presence or applicability of an answer.

Do not promote an operation vocabulary yet.

## Planned and observed patches

The review also strengthens the distinction between:

~~~text
planned patch
    = what answers are intended to change

observed patch
    = what answers actually changed
~~~

These may be represented by separate Update Documents or by states/relations between Updates.

Current evidence does not justify forcing one representation.

Hernán explicitly notes that there is no problem having N Update Documents for M or N changes across Q Documents.

## Reconciliation

An Update can preserve continuity between proposed and current knowledge:

~~~text
source answers
-> planned patch
-> execution
-> observed patch
-> resulting answers
~~~

If observed changes differ from planned ones, documentary continuity should preserve the actual result rather than rewriting history to match the plan.

## Relationship with Realization

For software-project continuity:

~~~text
Realization (current)
    = current state

Realization (proposed)
    = intended target state

Update
    = answer-level patch knowledge that describes transition work
~~~

Update should not duplicate the complete Realization state.

## Relationship with Drift

A planned Update that is not yet applied is not automatically Drift.

Drift becomes relevant when represented current knowledge and observed reality diverge without being reconciled.

An unapplied or partially applied Update may become evidence for Drift if the representation still claims a state that reality no longer matches.

## Relationship with repeated semantic subjects

Update provides another strong witness for repeated semantic subjects:

~~~text
one Update
    -> N patch operations
        -> each targets a specific answer
        -> each may carry the same subordinate questions
~~~

This should be compared with Domain Vocabulary terms and Consistency rules without assuming they share exactly the same semantic subject model.

## Open questions

- What gives an answer stable identity across wording changes?
- Can an Update target an unanswered question?
- Is adding an answer different from replacing an answer semantically?
- Can a patch target a repeated semantic subject plus one of its answers?
- Can one patch operation affect several answers atomically?
- Can one Update span several Documents?
- What makes several patch operations belong to the same Update?
- What information is required for documentary reversibility?
- Does reversal create a new Update rather than mutate history?
- How are conflicts between Updates represented?
- How are partially applied Updates represented?
- Should planned and observed Updates be separate Documents?
- How should Update relate to Decision when the patch changes during execution?

## Current status

Open research pin.

Do not reduce Update semantics to file editing, text replacement, or whole-Document replacement.

The strongest current hypothesis is:

> Update is a reversible semantic patch over documentary answers.
