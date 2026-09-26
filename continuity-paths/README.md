# Continuity Path definitions

This directory is reserved for the future normative Continuity Path definition language.

Continuity Paths are part of the intended VSlices Docs Standard surface, but their machine-consumable semantics have not yet been reviewed and promoted in this repository.

Historical research exists under `vslices/docs`, including the continuity-path artifacts developed before the current normative YAML model.

That material is evidence, not current normative syntax.

## Current status

Do not invent a Continuity Path YAML schema from the historical front-matter.

The next design pass should reconstruct the responsibility from real evidence in the same way Documents and Nexus definitions were reconstructed:

~~~text
historical artifacts
-> identify semantic responsibility
-> separate semantics from materialization
-> find the minimum executable definition language
-> document its coherence rules
-> promote only evidence-supported fields
-> register definitions in manifest.yaml
~~~

Until that review is complete, this directory intentionally contains no Continuity Path definitions.

## Expected responsibility boundary

The current research distinction is provisional:

~~~text
Document
    -> interrogates one target through one documentary responsibility

Nexus
    -> composes documentary perspectives around one target

Continuity Path
    -> connects knowledge across perspectives, transitions, or continuity of work
~~~

This wording is orientation only. It is not yet a normative Continuity Path specification.

When the family is promoted, this README should become the human- and AI-readable specification for creating and extending Continuity Path definitions, parallel to:

- `documents/README.md`
- `nexus/README.md`
