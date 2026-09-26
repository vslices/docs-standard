# VSlices Docs Standard

VSlices Docs Standard is the normative, versioned source for VSlices documentation artifact definitions.

Its purpose is to preserve useful knowledge across domain discovery, documentation, architecture, implementation, and system evolution without turning documentation into mandatory ceremony.

## Authority

The research and design history under `vslices/docs/es/alive-lab/research/notes/docs-standard/artifacts` is evidence used to develop this standard. It is not the normative source consumed by VSlices Tooling.

This repository defines the current semantic languages used to describe Documents, Nexus artifacts, and Continuity Paths in machine-consumable form.

`manifest.yaml` identifies definitions that have been explicitly promoted into the installed standard surface.

A definition may exist in this repository before being registered in the manifest when its language is understood but its concrete vocabulary is still expected to evolve through use.

VSlices Tooling may install and update a snapshot of this repository independently from Tooling itself.

## Extension entrypoints

This repository is intended to be understandable by a human or AI entering it without prior conversational context.

Each artifact family owns a README that specifies:

- its semantic responsibility;
- the current YAML shape;
- the meaning and authority of each field;
- coherence rules;
- how to create a new definition;
- how to extend an existing definition conservatively;
- which concerns remain deliberately unmodeled.

### Documents

Read:

- [`documents/README.md`](documents/README.md)

Documents interrogate knowledge about a target through a documentary responsibility.

Their definitions own root questions, subordinate question graphs, stable question identity, cardinality, admitted scopes, and other promoted Document semantics.

Current manifest-registered Document definitions live under `documents/*.yml`.

### Nexus

Read:

- [`nexus/README.md`](nexus/README.md)

Nexus definitions compose perspectives around a target.

They may also define optional open composition questions and recommendations for known Document or Nexus perspectives.

Recommendations are guidance, not requirements or a whitelist of what a concrete Nexus may associate.

Current candidate Nexus definitions live under `nexus/*.yml`.

They are intentionally not registered in `manifest.yaml` yet; their concrete vocabulary should continue to emerge through use.

### Continuity Paths

Read:

- [`continuity-paths/README.md`](continuity-paths/README.md)

Continuity Paths interrogate and navigate continuity.

Their definitions provide:

- a purpose;
- human-readable recommended traversal guidance;
- a root continuity question;
- an arbitrarily deep question graph;
- semantic connections between continuity points;
- recommendations for known Documents or Nexus definitions that can help preserve discovered knowledge.

The generated continuity graph is the mandatory semantic surface. Rendering belongs to Tooling.

Current candidate Continuity Path definitions live under `continuity-paths/*.yml`.

They reconstruct the historical Paths conservatively and are not registered in `manifest.yaml` yet.

## Definition languages

The YAML files in this repository are concrete machine-consumable syntax for Docs Standard semantics.

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

## Shared principle

The three families currently preserve different geometries:

~~~text
Document
    -> depth

Nexus
    -> composition

Continuity Path
    -> trajectory
~~~

Their mechanisms may overlap without collapsing their responsibilities.

For example, Nexus and Continuity Paths can both recommend known documentary structures, but recommendations remain open-world guidance rather than allowed-association lists.

## Research pins

Open transversal research remains under:

- [`pins/README.md`](pins/README.md)

Pins preserve uncertainty and design pressure that should not yet become executable vocabulary.

## Existing templates

The `templates/` directory predates the machine-consumable standard introduced here.

Those files remain useful historical and manual authoring references while their knowledge is evaluated and progressively promoted into normative definitions.

They must not be treated as authoritative merely because a template already exists.

## Design principle

VSlices Docs Standard owns documentary vocabulary and semantic definition languages.

VSlices Tooling owns the authoring, validation, discovery, persistence, and materialization mechanisms.

The standard may evolve independently through versioned definitions while Tooling remains responsible for realizing supported semantics.

## License

MIT
