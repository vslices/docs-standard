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

## Semantic update unit

Update review clarifies that an Update is not merely a bag of independent edits.

It is a semantic unit of change that may contain N patch operations over M Documents.

This raises an important question:

> What makes several answer-level patches belong to the same Update?

A useful provisional criterion is semantic cohesion rather than file location.

Patches may belong together because they jointly express one transition whose meaning would be incomplete or misleading if arbitrarily split.

This does not yet imply transactional or technical atomicity.

We should distinguish:

~~~text
semantic update unit
    = changes that belong together as one meaningful transition

technical atomicity
    = changes applied all-or-nothing by a mechanism
~~~

The first belongs to Docs Standard research. The second belongs to Tooling / realization unless semantic requirements later demand it.

## Reversible patch hypothesis

An Update should preserve enough semantic information to reconstruct:

~~~text
expected before state
-> semantic patch
-> resulting after state
~~~

without requiring a complete snapshot of the affected Documents.

The "before" state is not merely history. It also helps define applicability: if the target answer no longer corresponds to the expected source state, the patch may no longer be safely or meaningfully applicable.

This may make an Update reversible in the documentary sense.

Possible operations include, provisionally:

- add an answer;
- replace or revise an answer;
- remove an answer;
- possibly change the presence or applicability of an answer.

Do not promote an operation vocabulary yet.

## Applicability and invalidation

Update review distinguishes workflow timing from semantic applicability.

Questions such as "apply at iteration close" or "before publication" are Method / Tooling concerns unless they encode a real semantic precondition.

The semantic concern is:

> Under what source conditions is this patch still applicable?

Potential applicability knowledge includes:

- the answer identity being targeted;
- the expected answer state before patching;
- required related answers or semantic subjects;
- dependencies between patch operations;
- conditions that make the patch obsolete or conflicting.

This gives a stronger interpretation to the historical "causales de invalidación": invalidation is about the patch no longer matching the knowledge state it was designed to transform.

## Reversibility

Documentary reversibility means preserving enough information to understand and reconstruct the inverse semantic transition.

Open distinctions include:

- reversing the whole semantic Update versus one patch operation;
- exact restoration versus compensating change;
- semantic reversibility versus technical rollback;
- whether reversal should be represented as a new Update rather than history mutation.

The current requirement is semantic reversibility; implementation mechanics remain outside Docs Standard.

## Planned and observed patches

The review strengthens the distinction between:

~~~text
planned Update
    = answer changes intended to occur

observed Update
    = answer changes known to have occurred
~~~

Hernán's current working model favors allowing separate Update Documents for these roles rather than requiring one mutable Update lifecycle.

There is no semantic problem with N Update Documents describing M or N transitions over Q Documents.

This remains research rather than a normative cardinality rule.

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
- What makes several patch operations belong to the same semantic Update unit?
- Which patch operations must remain grouped for the transition to retain its meaning?
- Can an Update be semantically partial while still valid?
- What information is required for documentary reversibility?
- Does reversal create a new Update rather than mutate history?
- How are conflicts between Updates represented?
- How are partially applied Updates represented?
- Should planned and observed Updates be separate Documents?
- How should Update relate to Decision when the patch changes during execution?

## Promoted Update semantics

The current machine-consumable Update definition now promotes a reduced semantic graph around:

~~~text
What changes?
├─ what knowledge originates the update
├─ what makes the changes one semantic update unit
└─ which Documents and questions are affected
    ├─ why the question changes
    ├─ expected answer before
    └─ expected answer after
~~~

The YAML intentionally does not introduce a cardinality primitive yet.

Repeated affected Documents and repeated affected questions remain a semantic requirement under research until the common Document model can represent repeated semantic subjects explicitly.

The promoted definition also omits per-instance questions about partial application, completion, and atomicity because those are invariants of the Update type rather than variable knowledge each Update must answer.

## Current status

Open research pin with part of the Update semantics now promoted.

Do not reduce Update semantics to file editing, text replacement, or whole-Document replacement.

The strongest current hypothesis remains:

> Update is an irreducible, reversible semantic patch over documentary answers.
