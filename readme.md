# VSlices Docs Standard

VSlices Docs Standard is the normative, versioned source for VSlices documentation artifact definitions.

Its purpose is to preserve useful knowledge across domain discovery, documentation, architecture, implementation, and system evolution without turning documentation into mandatory ceremony.

## Authority

The research and design history under `vslices/docs/es/alive-lab/research/notes/docs-standard/artifacts` is evidence used to develop this standard. It is not the normative source consumed by VSlices Tooling.

This repository owns the current official vocabulary for Documents and Nexus definitions, and will progressively define Continuity Paths in the same machine-consumable form.

VSlices Tooling may install and update a snapshot of this repository in the same spirit that target Rulesets are installed and updated independently from Tooling itself.

## Current standard surface

`manifest.yaml` identifies the machine-consumable definitions that currently belong to the standard.

Current normative families:

- [Documents](documents/README.md)
- [Nexus](nexus/README.md)

Continuity Paths are the next family to reconstruct and promote. Their current entrypoint is:

- [Continuity Paths](continuity-paths/README.md)

Research pins remain available under:

- [Research pins](pins/README.md)

## How to extend the standard

This repository is intended to be understandable by a human or AI entering it without prior conversational context.

Each artifact family owns a README that specifies:

- its semantic responsibility;
- the current YAML shape;
- the meaning and authority of each field;
- coherence rules;
- how to create a new definition;
- how to extend an existing definition conservatively;
- which concerns remain deliberately unmodeled.

### Create or extend a Document

Read:

- [`documents/README.md`](documents/README.md)

Documents answer documentary questions about a target.

Their definitions own root questions, subordinate question graphs, stable question identity, cardinality, admitted scopes, and other promoted Document semantics.

Document definitions should grow through semantic pressure from real cases rather than speculative completeness.

### Create or extend a Nexus

Read:

- [`nexus/README.md`](nexus/README.md)

Nexus definitions compose existing documentary perspectives around a target.

Their current language defines Nexus type, admitted target scopes, recommended Document perspectives, and a human-readable explanation of the role each recommendation contributes.

Recommendations are optional and do not imply automatic Document creation.

### Create or extend a Continuity Path

Read:

- [`continuity-paths/README.md`](continuity-paths/README.md)

Continuity Paths have not yet completed the same semantic reconstruction.

The entrypoint deliberately explains what is known, what remains historical evidence, and how the future YAML language should be promoted without inventing semantics from old front-matter.

## Definition languages

The YAML files in this repository are the current concrete machine-consumable syntax for promoted Docs Standard semantics.

Their meaning is not defined only by field names. The corresponding family README is the human- and AI-readable semantic specification for that YAML language.

The intended direction is:

~~~text
semantic responsibility
-> family specification
-> machine-consumable YAML
-> Tooling validation and authoring
~~~

A future representation may lower these definitions to, or express them through, a more general semantic representation such as VSIR.

That possibility must not make the current YAML syntax or its semantics speculative. Changes should continue to be promoted from demonstrated needs.

## Progressive Documents

A Document specializes in one root question. Child questions progressively refine that question.

Creating a Document begins with only its root question and an unanswered placeholder. Once answered, immediate child questions become available. A child is materialized only when it receives a valid answer, and deeper questions become available progressively through the same cascade.

The complete question graph of a Document type is a space of possibilities, not a completion checklist. Questions that are not materialized are not missing work.

## Existing templates

The `templates/` directory predates the machine-consumable standard introduced here. Those files remain useful historical and manual authoring references while their knowledge is evaluated and progressively promoted into normative definitions.

They must not be treated as authoritative merely because a template already exists.

## Design principle

VSlices Docs Standard owns documentary vocabulary and semantic definition languages.

VSlices Tooling owns the authoring mechanism.

The standard may evolve independently through versioned definitions while Tooling remains responsible for loading, validating, discovering, updating, and materializing them.

## License

MIT
