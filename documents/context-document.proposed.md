# Context Document — cardinality proposal

This document explains the proposal captured in `context-document.proposed.yml`.

The proposal is intentionally **non-normative**. It exists to test a minimal way of representing repeated semantic subjects without confusing them with answers that merely contain multiple values.

The currently promoted definition remains `context-document.yml`.

## Problem being explored

Many questions can naturally produce several values:

~~~text
What actors participate?
    -> actor A
    -> actor B
    -> actor C
~~~

That does not necessarily mean each actor must become a repeated semantic subject in the Document model.

The distinction under investigation is:

~~~text
answer cardinality
!=
semantic subject cardinality
~~~

A question should introduce repeated semantic subjects only when the individual elements need semantic identity of their own.

Typical evidence includes:

- each element receives the same subordinate questions;
- another question needs to reference an element individually;
- losing the identity of each element would lose relevant meaning.

A plural answer alone is not enough.

## Proposed primitive: subjects

The proposal introduces a small `subjects` construct.

Example:

~~~yaml
- id: assumptions
  text: ¿Qué supuestos estamos haciendo?

  subjects:
    id: assumption
    cardinality:
      min: 0

    question:
      id: assumption
      text: ¿Qué supuesto estamos haciendo?
      children:
        ...
~~~

Semantically:

~~~text
question
    -> introduces zero or more semantic subjects

each subject
    -> has its own identity
    -> receives the same question subtree
~~~

The proposal deliberately does not define storage, rendering, identifiers, ordering, uniqueness, or CLI interaction mechanics.

Those belong to later design work unless semantic evidence requires them.

## Why cardinality does not live directly on every question

A question such as:

> ¿Qué actores participan o se ven afectados?

may naturally have several answers.

That can remain:

~~~text
one question
-> several answer values
~~~

There is no need to introduce repeated subjects unless each actor must later be interrogated or referenced individually.

By contrast:

> ¿Qué supuestos estamos haciendo?

currently has a subordinate family that only makes sense **per assumption**:

~~~text
Assumption A
├─ Why do we accept it?
├─ What uncertainty remains?
├─ What depends on it?
└─ What changes if it is false?

Assumption B
├─ Why do we accept it?
├─ What uncertainty remains?
├─ What depends on it?
└─ What changes if it is false?
~~~

This is subject cardinality rather than merely answer cardinality.

## Cardinality in the proposal

The proposal uses only:

~~~yaml
cardinality:
  min: N
~~~

Absence of `max` means that no maximum is currently declared.

This is intentionally smaller than introducing a complete cardinality language.

If real Documents later require:

~~~text
exactly one
zero or one
one to three
at least two
bounded maximums
~~~

the language can be extended from evidence.

## Perspective

### Why it becomes a repeated subject

The promoted Context graph currently treats one perspective as primary:

~~~text
From what perspective do we observe this context?
├─ Who observes?
├─ What can be observed?
├─ What may remain outside the perspective?
└─ How would interpretation change from another perspective?
~~~

This creates an asymmetry between one unnamed primary perspective and all other possible perspectives.

The proposal instead models:

~~~text
Context
-> 1:N Perspective
~~~

Each Perspective receives:

~~~text
What perspective are we describing?
Who observes or interprets from this perspective?
What part of the context is observable from this perspective?
What part may remain outside this perspective?
What interpretation does this perspective produce?
~~~

### Proposed cardinality

~~~yaml
cardinality:
  min: 1
~~~

The current hypothesis is that a Context is always represented from at least one perspective.

This remains a proposal rather than a promoted invariant.

## Assumption

### Why it becomes a repeated subject

The current tree already implies a repeated structure:

~~~text
What assumption are we making?
├─ Why do we accept it?
├─ What uncertainty remains?
├─ What depends on it?
└─ What changes if it is false?
~~~

A Context may contain several assumptions, and each one needs its own answers.

Therefore:

~~~text
Context
-> 0:N Assumption
~~~

### Proposed cardinality

~~~yaml
cardinality:
  min: 0
~~~

A Context can contain no explicit assumptions, so the proposal does not require at least one.

## Open Question

### Why it becomes a repeated subject

The current unresolved-context branch also implies a repeated semantic subject:

~~~text
What question remains open?
├─ Why can we not answer it yet?
├─ What evidence is missing?
├─ What depends on resolving it?
└─ What risk exists if we act without resolving it?
~~~

Each unresolved question has its own reason, missing evidence, dependencies, and action risk.

Therefore:

~~~text
Context
-> 0:N Open Question
~~~

### Proposed cardinality

~~~yaml
cardinality:
  min: 0
~~~

A Context may currently have no known unresolved questions.

## Questions that remain ordinary multiple answers

The proposal intentionally does **not** introduce subjects for every plural question.

Examples include:

~~~text
What conditions currently exist?
What tensions or frictions exist?
What actors participate?
What systems or tools intervene?
What processes or activities intervene?
What observations support this context?
What sources support it?
What known exceptions exist?
~~~

These questions may produce multiple values, but the current graph does not require each value to carry its own subordinate semantic structure.

They remain ordinary questions unless later evidence shows that their answer elements need stable subject identity.

## Resulting Context geometry

The proposed graph contains three explicit repeated-subject families:

~~~text
Context
├─ 1:N Perspective
├─ 0:N Assumption
└─ 0:N Open Question
~~~

Other plural answers remain answer cardinality rather than subject cardinality.

## CLI interpretation hypothesis

A CLI could interpret a subject-producing question differently from an ordinary question.

Ordinary question:

~~~text
What actors participate?
> [multiple values in one answer]
~~~

Subject-producing question:

~~~text
What assumptions are we making?

[Add assumption]

Assumption 1
  What assumption are we making?
  Why do we accept it?
  What uncertainty remains?
  ...

Assumption 2
  ...
~~~

This is only an interaction hypothesis.

The YAML proposal defines the semantic distinction; Tooling remains responsible for deciding how that distinction is authored and persisted.

## Open questions

- Does every repeated subject require stable identity beyond its position in the answer?
- Should `subjects.id` identify a semantic subject type or a local subject role?
- Is `subjects.question` the right shape, or should a repeated subject itself be a first-class question node?
- Is `min: 1` truly an invariant for Perspective?
- Should cardinality eventually support maximums?
- Do repeated subjects need explicit ordering semantics?
- How should relations between repeated subjects be represented?
- Can a repeated subject reference a subject introduced by another question?
- How should nested repeated subjects be represented in the CLI?
- Which parts belong to Docs Standard semantics and which belong exclusively to Tooling?

## Working criterion

> A plural answer does not justify explicit subject cardinality by itself.

Explicit cardinality becomes useful when the multiplicity belongs to identifiable semantic subjects whose individual identity matters for further interrogation or relationships.
