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
