# Document front-matter

This document defines the current semantic identity carried by a VSlices Document artifact.

It is intentionally smaller than the front-matter explored in `vslices/docs`. The research surface remains evidence and design history; fields are promoted here only when the executable authoring model gives them a demonstrated responsibility.

## Current persisted identity

A newly created Document currently persists only its artifact family and Document type:

```yaml
---
artifact:
  kind: document
  type: context
---
```

The same shape applies to every Document type. For example, a Structure Document changes only the type:

```yaml
---
artifact:
  kind: document
  type: structure
---
```

### `artifact.kind`

Identifies the artifact family.

For the artifacts governed by this directory its value is `document`.

The artifact carries this value because the Markdown file must remain self-describing independently of its filename or location.

### `artifact.type`

Identifies the stable Document type whose vocabulary is resolved through the installed Docs Standard.

The artifact persists the type identity, not the type definition.

For example, `artifact.type: context` allows Tooling to resolve the Context definition and recover its root question, descendants, admitted scopes, and other type-owned semantics from the installed standard.

## Question identity

The front-matter does not list the questions materialized in the Document.

Each materialized question carries its own stable question identity in Tooling-managed hidden metadata next to its answer. The visible question text is resolved from Docs Standard and is not semantic identity.

This gives the artifact two complementary identity layers:

```text
front-matter
  -> what Document type is this?

question metadata
  -> which questions from that type are materialized?
```

Neither layer should duplicate the vocabulary owned by Docs Standard.

## Authority classification

The broader front-matter explored during research is classified as follows for the current authoring model:

| Field | Current status | Authority / reason |
| --- | --- | --- |
| `artifact.kind` | persisted | Artifact family identity required for a self-describing file. |
| `artifact.type` | persisted | Stable reference to a Document definition owned by Docs Standard. |
| `artifact.scope` | deferred | Semantic metadata may be useful, but the authoring need and transition have not yet been demonstrated. Admitted values remain type-owned vocabulary. |
| `artifact.target` | deferred | Likely semantic identity/context, but no current authoring transition requires it. |
| `artifact.language` | deferred | Potential artifact metadata; not required to reconstruct the current progressive Document state. |
| `metadata.status` | deferred | Lifecycle semantics should be introduced from a real lifecycle case. |
| `metadata.relates` | deferred | Relations require a stable artifact-reference model that has not yet been established here. |
| `document.question` | derived, not persisted | The root question is owned by the Document definition in Docs Standard. Persisting its text would create a second source of truth. |
| `tooling.schema.version` | deferred | Introduce only when the persisted artifact schema actually needs versioned interpretation or migration. |
| `tooling.template.*` | not part of the current model | Progressive Documents are not instances of a rigid template. Tooling materializes the currently traversed question surface. |

Deferred does not mean rejected. It means the current evidence does not justify making the field part of the required persisted contract yet.

## Invariants

1. A VSlices Document must be able to identify its artifact family and Document type without depending on its filename, path, visible heading text, or current Docs Standard wording.
2. Docs Standard owns Document vocabulary: type definitions, stable question ids, question text, question relationships, admitted scopes, and other type-specific constraints.
3. Tooling owns the authoring and materialization mechanism.
4. Visible question text is not durable identity.
5. The root question must not be copied into front-matter when it can be resolved from `artifact.type`.
6. A question block must not repeat Document type identity when the artifact front-matter already establishes it.
7. Adding ordinary questions or changing question wording in Docs Standard must not require rewriting the artifact front-matter schema.
8. Fields should be promoted into persisted front-matter only when a real authoring or reconstruction requirement needs them.

## Compatibility

Early experimental Documents encoded the Document type repeatedly inside Tooling-managed question or placeholder comments.

Tooling may continue to read that representation as a compatibility bridge, but newly materialized Documents should use front-matter as the artifact-level identity source and keep question metadata limited to stable question identity.

Compatibility syntax is a Tooling concern, not normative Document vocabulary.
