# VSlices Docs Standard

VSlices Docs Standard is the normative, versioned source for VSlices documentation artifact definitions.

Its purpose is to preserve useful knowledge across domain discovery, documentation, architecture, implementation, and system evolution without turning documentation into mandatory ceremony.

## Authority

The research and design history under `vslices/docs/es/alive-lab/research/notes/docs-standard/artifacts` is evidence used to develop this standard. It is not the normative source consumed by VSlices Tooling.

This repository owns the current official document vocabulary and will progressively define Documents, Nexus artifacts, and Continuity Paths in a machine-consumable form.

VSlices Tooling may install and update a snapshot of this repository in the same spirit that target Rulesets are installed and updated independently from Tooling itself.

## Current standard surface

`manifest.yaml` identifies the definitions that currently belong to the standard.

The first normative family being materialized is `Document`:

- [`documents/README.md`](documents/README.md) defines the progressive question-cascade model shared by Documents.
- [`documents/context-document.yml`](documents/context-document.yml) is the first machine-consumable Document type definition.

The initial Context Document intentionally contains only two questions. The goal is to prove the authoring mechanism before expanding the vocabulary:

```text
¿Dónde existe?
└─ ¿Qué estamos asumiendo como cierto?
```

Adding further Context questions should be a Docs Standard change, not a Tooling code change.

## Progressive Documents

A Document specializes in one root question. Child questions progressively refine that question.

Creating a Document begins with only its root question and an unanswered placeholder. Once answered, immediate child questions become available. A child is materialized only when it receives a valid answer, and deeper questions become available progressively through the same cascade.

The complete question graph of a Document type is a space of possibilities, not a completion checklist. Questions that are not materialized are not missing work.

## Existing templates

The `templates/` directory predates the machine-consumable standard introduced here. Those files remain useful historical and manual authoring references while their knowledge is evaluated and progressively promoted into normative definitions.

They must not be treated as authoritative merely because a template already exists.

## Design principle

VSlices Docs Standard owns the document vocabulary.

VSlices Tooling owns the document authoring mechanism.

The standard may evolve independently through versioned definitions while Tooling remains responsible for loading, validating, discovering, updating, and materializing them.

## License

MIT
