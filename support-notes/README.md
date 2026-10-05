# Support Note definitions

This directory specifies the current semantic definition language for Support Notes.

A Support Note preserves auxiliary knowledge that should not be lost yet, without forcing that knowledge prematurely into a Document responsibility.

It is a distinct artifact family.

The current responsibility boundary is:

~~~text
Document
    -> explains knowledge through one primary documentary responsibility

Support Note
    -> supports, records or references auxiliary knowledge
    -> may preserve incomplete or provisional knowledge
    -> may later feed, refine or be promoted into a Document

Nexus
    -> composes perspectives around one target

Continuity Path
    -> interrogates and navigates continuity
~~~

A Support Note is therefore not a "small Document".

Its value is precisely that useful knowledge can be preserved before there is enough stability, authority, reuse or documentary responsibility to justify a Document.

## Evidence and promotion status

The historical Docs Standard research recognized Support Note as its own family and explored several types.

The current Software Migration run for external payment requests provides direct real-use pressure for four of them:

~~~text
draft
result
validation
risk
~~~

Two additional historical candidates remain known:

~~~text
testing-spec
external
~~~

They are not promoted by this reconstruction merely because historical templates exist. Their current semantics should be re-evaluated from real use before they become part of the normative definition set.

## Definition language

The current language is intentionally small.

~~~yaml
kind: vslices-support-note-definition
version: 0.1

support-note:
  type: draft

  question:
    id: draft
    text: ¿Qué estamos esbozando?
~~~

Only semantics supported by demonstrated use should be added.

### kind

Identifies the definition family.

For definitions in this directory:

~~~yaml
kind: vslices-support-note-definition
~~~

### version

Identifies the current Support Note definition-language version:

~~~yaml
version: 0.1
~~~

### support-note.type

Stable identity of the Support Note type.

The initial evidenced types are:

~~~text
draft
result
validation
risk
~~~

Tooling should resolve Support Note vocabulary through this identity rather than through filenames or rendered headings.

### support-note.question

Defines the auxiliary question owned by the Support Note type.

Every question has:

~~~yaml
id: stable-question-id
text: Human-readable question
~~~

Question text is human-readable vocabulary.

Question id is stable semantic identity.

A Support Note question is not a primary documentary question. If the useful knowledge being preserved grows until it answers a primary documentary responsibility, that is pressure to move or promote the knowledge into the corresponding Document rather than expanding Support Note until it behaves like one.

## Current evidenced types

### draft

~~~text
Question:
¿Qué estamos esbozando?
~~~

Responsibility:

Preserve an emerging model, idea, hypothesis, fragment or interpretation that is useful enough to keep but is not yet stable enough to own a primary documentary responsibility.

The external-payment-requests migration currently pressures this type through:

- the integrated candidate flow for preparing and first submitting an EP;
- the provisional interpretation of DS 49 document requirements and their future variation by decree;
- the deferred reconstruction of resubmission after repairs.

A Draft Support Note may contain open questions and partial knowledge.

It must not imply that the modeled flow, rule or interpretation is already institutionally confirmed or complete.

### result

~~~text
Question:
¿Qué obtuvimos?
~~~

Responsibility:

Record what was observed or obtained by applying, inspecting, executing, testing, using or reviewing something, without yet interpreting that result against a separate criterion.

The external-payment-requests migration currently pressures this type through results such as:

- the normal external advance route validates one financial line in the inspected path;
- the aggregate project validation found in the snapshot is connected to import rather than that normal external route;
- the observed classification logic for payment-request types;
- the observed submission command does not carry a separate acceptance value.

A Result Support Note preserves occurrence or observation.

It must not silently turn the observation into a judgment about correctness, institutional intent or target behavior.

### validation

~~~text
Question:
¿Qué significa lo obtenido frente a un criterio?
~~~

Responsibility:

Interpret a result against an explicit criterion, expectation, rule or target condition.

The external-payment-requests migration currently pressures this type through comparisons such as:

- observed per-line validation versus the confirmed target rule of both project and line limits;
- observed payment-request classification versus the operational rule currently being reconstructed;
- observed required-file behavior versus the proposed or confirmed requirement for a final warranty payment.

A Validation Support Note requires both:

~~~text
result
+
criterion
~~~

The criterion must retain its authority and epistemic status.

Validation does not transform a provisional criterion into institutional truth merely by using it.

### risk

~~~text
Question:
¿Qué podría salir mal?
~~~

Responsibility:

Preserve a plausible failure, inconsistency, loss, ambiguity or harmful condition associated with the supported knowledge or realization.

The external-payment-requests migration currently pressures this type through risks such as:

- folder and office creation depends on handlers whose dispatch, ordering, retry and immediacy guarantees have not been verified;
- file-system and database operations may leave partial state when background files are uploaded or removed;
- a financial advance can be persisted before its warranty document is stored.

A Risk Support Note should distinguish:

~~~text
observed mechanism or condition
-> plausible failure
-> possible consequence
~~~

when those parts are known.

A missing verification is not automatically a risk. The note should state the failure mode that makes the uncertainty materially relevant.

## Relationship between Result and Validation

The distinction between Result and Validation is deliberate.

~~~text
Result
    = what happened / what was obtained

Validation
    = what that result means against a criterion
~~~

For example:

~~~text
Result:
the inspected external route validates the accumulated percentage of one financial line

Criterion:
the target operation requires a 95% limit at both project and line level

Validation:
the inspected route does not by itself demonstrate enforcement of the complete target rule
~~~

Keeping these responsibilities separate prevents an observation from inheriting a judgment or authority that its evidence does not support.

## Relationship with migration reports and findings

A migration report and a Support Note have different responsibilities.

~~~text
migration report
    -> preserves the investigation, evidence, uncertainty and progression of a concrete run

Support Note
    -> preserves auxiliary knowledge that should remain findable and reusable beyond that report's narrative
~~~

A report does not need to be converted wholesale into Support Notes.

Extract only knowledge whose continued availability matters independently of the report.

Likewise, a finding may contain both a Result and a Validation in one run-local record. That does not collapse the Support Note responsibilities if the knowledge is later preserved as reusable documentary artifacts.

## Relationship with Documents

Support Notes exist to avoid both knowledge loss and premature formalization.

A useful progression can be:

~~~text
observation / inference / question
-> Support Note
-> repeated use, confirmation or stable responsibility
-> Document
~~~

Promotion is not mandatory.

A Support Note may instead be superseded, archived, remain local, or continue supporting another artifact.

The promotion test is responsibility, not size.

If the note has grown until it principally answers a question such as:

~~~text
¿Dónde existe?
¿Qué debe ocurrir?
¿Qué debe respetar?
¿Qué se decidió?
~~~

then the knowledge probably belongs in the corresponding Document family.

## Definition versus artifact instance

This repository owns Support Note vocabulary and definition semantics.

It does not yet define the complete persisted instance contract for Support Notes.

Historical research explored fields such as:

~~~text
scope
target
language
status
relations
supports
tooling schema/template metadata
~~~

Those fields must not be copied into the normative language solely because an older template contained them.

Their promotion should follow current Docs Standard boundaries and real authoring pressure.

The same applies to searchable metadata such as tags: operational discovery may justify such metadata, but search metadata does not gain documentary semantic authority merely because it is useful.

## Creating or extending a Support Note definition

Start from real auxiliary knowledge that repeatedly needs to be preserved before a Document is justified.

Ask:

~~~text
What useful knowledge would otherwise be lost?
Why is a Document premature or the wrong responsibility?
What auxiliary question does this Support Note type own?
Does another existing Support Note type already own that question?
Does the note preserve an observation, an interpretation, a risk, or an emerging model?
Would promotion to a Document better preserve the knowledge now?
~~~

Create or extend only the smallest semantics demonstrated by real use.

Do not reconstruct historical templates wholesale for completeness.

## Conservative reconstruction loop

~~~text
observe real work
-> identify auxiliary knowledge that should survive
-> test an existing Support Note question against it
-> note where the question is insufficient or ambiguous
-> refine only the smallest missing distinction
-> test again against another real case
-> promote semantics when evidence remains useful
~~~

The current external-payment-requests migration is one such pressure source.

Historical Docs Standard research remains evidence and design history, not current authority by itself.
