# Continuity Path definitions

This directory specifies the current YAML language for Continuity Path definitions.

A Continuity Path is a navigation-oriented interrogation of continuity.

It defines a question graph that helps an author discover how one point of knowledge relates to another and recommends known Docs Standard perspectives that can preserve the discovered continuity.

The current distinction is:

~~~text
Document
    -> interrogates knowledge about a target
    -> deepens documentary understanding

Nexus
    -> composes perspectives around a target

Continuity Path
    -> interrogates continuity
    -> builds a navigable trajectory
    -> recommends ways to preserve knowledge at points in that trajectory
~~~

A Continuity Path is not classified as Core, Supporting, or Contextual by intrinsic type.

Those labels describe how a Path participates in a particular continuity situation, not what the Path definition is.

## Generated surface

A generated Continuity Path currently needs only two conceptual sections:

~~~text
Purpose of the traversal

Continuity diagram
    -> recommended traversal
    -> generated path graph
~~~

The graph is the mandatory semantic surface.

The concrete diagram syntax and rendering mechanism belong to Tooling.

Mermaid is not part of the definition language.

## YAML shape

~~~yaml
kind: vslices-continuity-path-definition
version: 0.1

continuity-path:
  type: business-driver

  purpose: >
    Preserva continuidad entre un elemento y la situación de negocio
    que lo origina, justifica o condiciona.

  recommended-traversal: >
    Comenzar por la situación de negocio y avanzar hacia la necesidad,
    las consecuencias, las restricciones y las respuestas relacionadas.

  question:
    id: business-driver
    text: ¿Qué situación de negocio origina, justifica o condiciona esto?

    children:
      - id: business-need
        text: ¿Qué dolor, necesidad u oportunidad intenta responder?

        connection:
          text: responde a

        recommendations:
          - document: context
            role: Preserva el contexto de la necesidad
~~~

## Definition identity

### `kind`

For definitions in this directory:

~~~yaml
kind: vslices-continuity-path-definition
~~~

### `version`

Identifies the definition-language version.

~~~yaml
version: 0.1
~~~

### `continuity-path.type`

Stable identity of the Continuity Path definition.

It identifies vocabulary, not whether the Path is Core, Supporting, or Contextual in a concrete continuity situation.

## Purpose

`purpose` is human-readable text explaining what continuity this Path helps preserve and why the traversal exists.

It is not part of the generated graph and does not replace the root continuity question.

## Recommended traversal

`recommended-traversal` is human-readable navigation guidance.

It can explain a useful way to traverse the graph without making that traversal mandatory.

~~~text
recommended traversal
    = navigation guidance

recommended traversal
    != graph semantics
    != required total order
~~~

A Path may branch, converge, or expose several useful routes.

The graph remains authoritative for the available continuity questions and relationships.

## Question graph

`continuity-path.question` is the root continuity question.

A question may contain arbitrarily deep `children`.

~~~text
Question
├─ Question
│  ├─ Question
│  │  └─ ...
│  └─ Question
└─ Question
~~~

Question depth represents semantic refinement of the continuity being explored, not Markdown heading depth or diagram indentation.

### Question identity

Every question has:

~~~yaml
id: stable-question-id
text: Human-readable question
~~~

The `id` is stable semantic identity.

The `text` may improve while preserving identity when the responsibility of the question does not change.

### Optional default

A question may provide an optional authoring default:

~~~yaml
default: <value>
~~~

The default is a suggestion for authoring when a common initial value exists.

It is not immutable semantics and may be replaced by a concrete instance.

For diagram questions, the default does not introduce a separate free-text answer model. The continuity representation is still oriented through discovered nodes, relations, and associated/recommended artifacts.

Use defaults conservatively and only when real cases demonstrate a useful common value.

## Connections

A non-root question may explain how the continuity point it discovers relates to its parent through:

~~~yaml
connection:
  text: justifica
~~~

The connection text is semantic.

It exists because two discovered points may be connected in materially different ways:

~~~text
A -- justifica --> B
A -- depende de --> C
A -- condiciona --> D
~~~

Tooling may render these relationships in a diagram, but the rendering syntax is not normative.

A connection is optional when the relationship is obvious or not yet known.

## Recommendations

A question may recommend known Docs Standard perspectives that can help preserve the knowledge discovered at that point.

~~~yaml
recommendations:
  - document: context
    role: Preserva el contexto necesario para entender este punto

  - nexus: capability
    role: Compone las perspectivas necesarias para entender la capacidad descubierta
~~~

A recommendation entry currently references exactly one known definition family:

~~~text
document: <document-type>
or
nexus: <nexus-type>
~~~

### Recommendations are the standard's guidance, not the answer universe

In the generated diagram, there is no independent free-text answer block analogous to a Document answer.

The Path orients the author through continuity points and recommends known documentary structures that can preserve what was discovered.

However, recommendations do not constrain the concrete representation.

~~~text
recommendations
    = known guidance for preserving continuity

recommendations
    != whitelist
    != complete set of possible associations
~~~

A concrete Continuity Path may associate artifacts, references, representations, or knowledge outside these recommendations.

Those associations belong to the concrete representation, not to the definition vocabulary.

For this reason the definition language does not provide an `artifact`, `other`, or catch-all recommendation kind.

### `role`

`role` explains why the recommended Document or Nexus may help at this point in the trajectory.

It is human-readable guidance, not persisted artifact identity.

## Progressive use

A Continuity Path does not require every defined question to be traversed.

The complete question graph is a space of possible continuity exploration, not a completion checklist.

Unvisited questions are not documentary debt.

Tooling may expose the root and progressively reveal relevant children as the author navigates the continuity.

## Creating a new Continuity Path definition

Start from a real continuity problem.

Ask:

~~~text
What continuity are we trying not to lose?
What root question exposes that continuity?
What next questions repeatedly reveal useful continuity points?
How are those points related?
Which existing Documents or Nexus definitions help preserve them?
What navigation guidance genuinely helps without becoming a rigid workflow?
~~~

Create the smallest question graph supported by evidence.

Do not reproduce an entire historical template merely because it exists.

## Extending an existing Continuity Path definition

Extend from observed use.

A candidate question deserves consideration when:

- authors repeatedly need the same next continuity question;
- the current graph hides a materially important transition or relationship;
- a recurring continuity point cannot be reached cleanly;
- a known Document or Nexus perspective repeatedly becomes useful at the same point;
- the current graph forces unrelated knowledge into the wrong question.

Before adding a question, ask:

~~~text
Does this continue the same continuity responsibility?
Does it reveal a new continuity point or relation?
Would it instead belong to a Document?
Would it instead be a Nexus composition concern?
Does the connection text expose a meaningful relation?
Is the recommendation guidance rather than a requirement?
~~~

## Conservative extension loop

~~~text
use the Path in a real case
-> traverse until continuity becomes unclear
-> identify the missing question, node, or relation
-> formulate the smallest useful addition
-> recommend only known perspectives that genuinely help
-> test it in another case
-> promote if the distinction remains useful
-> traverse again
~~~

## Semantic boundary

The most important ownership test is:

~~~text
If the question asks:
"What is true about this target?"
    -> likely Document

If it asks:
"What perspectives explain this target together?"
    -> likely Nexus

If it asks:
"Where does this continuity go next, and how is it related?"
    -> likely Continuity Path
~~~

## Current candidate definitions

This directory contains minimal reconstructions of the historical Continuity Paths from `vslices/docs`.

They intentionally preserve only:

- purpose;
- recommended traversal;
- root continuity question;
- the demonstrated question trajectory;
- connection labels where useful;
- minimal recommendations from known Docs Standard vocabulary.

Historical tables, front-matter, rendering details, auxiliary sections, and exhaustive artifact lists are not carried forward automatically.

The definitions should continue to evolve from use.
