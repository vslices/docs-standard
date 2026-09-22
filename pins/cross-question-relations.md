# Relationships between questions outside the parent-child tree

## Research question

> Does Docs Standard need semantic relationships between questions that are related but do not belong in a direct parent-child hierarchy?

## Observation

The current model primarily expresses refinement through parent-child relationships.

Domain Vocabulary exposed a case where questions form a semantic cluster without one naturally owning the others.

~~~text
confusable-terms
    -> identifies which terms are involved

apparent-equivalence
    -> explains why they appear equivalent

semantic-difference
    -> explains what separates them
~~~

These are related like semantic cousins rather than a simple refinement chain.

## Working distinction

~~~text
tree relationship
    = one question refines another

cross-question relationship
    = one question depends on, contextualizes, contrasts with,
      or otherwise relates to another without being its child
~~~

Without cross-question relations we may be forced to duplicate questions, place them under unnatural parents, or rely on implicit human inference.

## Candidate relationship vocabulary

Do not promote any vocabulary yet.

Possible relations to test:

- depends on;
- contextualizes;
- contrasts with;
- provides evidence for;
- should be considered with;
- requires the subject introduced by.

## Relationship with repeated subjects

Cross-question relationships may need to reference both question identity and semantic subject identity.

Example:

~~~text
term A
    -> confusable with term B

apparent-equivalence
    -> relationship specifically between A and B
~~~

## Open questions

- Should question graphs remain trees plus optional semantic edges?
- Which relations are semantic rather than authoring convenience?
- Can a question relate to one in another Document?
- Do these relations affect availability or only interpretation?
- Should Tooling recommend related questions using these edges?
- How should cycles be handled?

## Current status

Open research pin.

Domain Vocabulary apparent-equivalence is the first explicit witness.