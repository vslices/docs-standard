# Action Flow

## Status

Candidate.

## Purpose

An **Action Flow** represents ordered work as actions, conditions, consequences, participants, and relevant relationships between actions.

Its purpose is to make work understandable at the level appropriate to the current question without prematurely forcing that work into a technical realization.

Action Flow is a visual notation candidate, not a new source of business truth.

The knowledge represented by the diagram should remain grounded in the artifacts, evidence, and authorities that explain the work.

## Two projections

Action Flow currently has two complementary projections:

```text
Abstract Action Flow

Systematized Action Flow
```

They observe the same work from different levels of realization.

### Abstract Action Flow

An **Abstract Action Flow** represents what work must happen without committing to where or how the system realizes it.

It may show:

- actions;
- ordering;
- conditions;
- cardinality;
- consequences;
- initiating actors when semantically relevant;
- handoffs;
- alternative or repeated paths.

It should avoid introducing implementation responsibilities that are not necessary to explain the work.

Example:

```text
Create Payment Request
-> Folder exists for the request
-> Office exists for the request
```

An abstract flow may be useful even when no software implementation exists.

### Systematized Action Flow

A **Systematized Action Flow** represents how the work is realized, or proposed to be realized, by human roles and system responsibilities.

It adds explicit realization lanes.

Typical lanes may include:

```text
Human
  External User
  Internal User

System
  View
  Product / BFF
  Service
  Worker
  Provider
  Integration
```

The lane taxonomy is contextual. A diagram should expose responsibilities at the smallest level useful for the decision being made.

It does not need to descend automatically to repository, project, class, or file level.

Example:

```text
External User | View | Payment Request | Folder | Office
---------------------------------------------------------
Search project
              | query
Select reviewer
              | submit
                       | create request
                       | publish event
                                         | create folder
                                                  | create office
Choose next navigation
```

A Systematized Action Flow may represent either:

- the current implementation;
- a proposed target realization.

The diagram must make that state explicit.

## Relationship between both projections

The relation is not one-to-one.

One abstract action may require several system actions:

```text
Abstract action
    -> 1..N systematized actions
```

A system action may also exist only to support realization:

```text
system action
    -> no independent business action
```

Examples include:

- opening a modal;
- serializing a request;
- retrying a provider call;
- refreshing a cache;
- redirecting a route;
- persisting an integration token.

Do not invent abstract business meaning merely to justify a realization-support action.

## Work hierarchy and useful limits

Action Flows participate in the current work hierarchy:

```text
Scenario
  -> Work Lines
      -> Work Processes
          -> Work Flows
              -> Work Steps
```

The hierarchy has two useful directions.

### Organizational decomposition

```text
Scenario
-> Work Line
-> Work Process
-> Work Flow
```

This direction explains progressively smaller units of coordinated work.

#### Work Line

A Work Line commonly coordinates work across several areas, departments, roles, or responsibilities.

Because of that, it is primarily organizational.

It may be represented using Abstract Action Flows to show the major movement of work.

Trying to systematize the whole line may be useful for architecture or integration analysis, but the line itself should not be assumed to correspond to one software realization.

#### Work Process

A Work Process composes several meaningful actions into a recognizable business progression.

At this level it becomes useful to distinguish:

- opaque actions whose internal realization is not currently relevant;
- actors or roles allowed to perform actions;
- conditions;
- consequences;
- handoffs;
- calls into system-owned capabilities.

A Product Feature that composes multiple Service actions may correspond naturally to this level.

#### Work Flow

A Work Flow is closer to cause and effect.

It normally has a triggering actor or condition and describes a bounded sequence that produces an outcome.

The initiating actor may be:

- inside the represented flow;
- outside it, when another process or system triggers the flow.

A Service Feature that represents one opaque and atomic action commonly has affinity with this level.

A Product Feature that delegates exactly one meaningful Service action may also have affinity with this level.

### Realization decomposition

The opposite direction begins from concrete realization:

```text
Work Step
-> Work Flow
-> Work Process
```

#### Work Step

A Work Step is implementation-close.

It answers questions such as:

```text
If Create Ticket is decomposed,
what executable steps occur and in what order?
```

Examples may include:

- validate input;
- load aggregate;
- evaluate invariant;
- persist state;
- publish event;
- return result.

This level commonly belongs to Systematized Action Flow or executable behavior documentation.

#### Why the useful limit stops near Process

As realization is composed upward, several Work Flows may reveal a Work Process.

Going beyond a Process into a Work Line usually requires organizational knowledge about coordination between multiple actors, areas, departments, priorities, or responsibilities.

That knowledge cannot be derived safely from software realization alone.

Therefore:

```text
Abstract decomposition can travel naturally:
Line -> Process -> Flow

Realization composition can travel naturally:
Step -> Flow -> Process

Neither direction should pretend it can infer the whole other side automatically.
```

## Action semantics

An action should identify at least:

- what happens;
- who or what performs it when relevant;
- what must already be true when relevant;
- what result or consequence matters.

An action should be named from the work being performed, not from incidental implementation syntax.

Prefer:

```text
Create Payment Request
Validate required files
Persist Office
Notify reviewer
```

over:

```text
Call HandleAsync
Invoke endpoint
Execute SQL
Open component
```

unless the implementation mechanism itself is the subject being analyzed.

## Relationships

The minimal candidate relationships are:

```text
A -> B
    B follows A

A -[condition]-> B
    B follows A when the condition holds

A -> {B, C}
    A causes or enables multiple actions

{A, B} -> C
    C requires multiple prior actions or outcomes

A ->* B
    B may repeat

A ->? B
    B is optional
```

This syntax is conceptual. Rendering syntax is not yet normative.

Cardinality may be attached when it preserves important meaning:

```text
Payment Request
-> exactly 1 Folder
-> exactly 1 Office
```

## Lanes in Systematized Action Flow

A Systematized Action Flow should use two-dimensional lanes when responsibility matters.

One dimension is action progression.

The second dimension is responsibility.

Recommended high-level grouping:

```text
Human responsibilities
System responsibilities
```

Human lanes may distinguish role:

```text
External User
Reviewer
Internal Operator
Supervisor
```

System lanes may distinguish semantic realization responsibility:

```text
View
Product / BFF
Service
Worker
External Provider
```

Prefer responsibility over physical deployment.

For example, use `Payment Request Service` when the relevant question is semantic ownership rather than `PaymentRequests.Core.dll`.

Concrete files, endpoints, classes, or repositories may be linked as implementation evidence without becoming the lane identity.

## Current vs proposed realization

A Systematized Action Flow must make clear whether it represents:

```text
Observed current realization

or

Proposed target realization
```

Do not visually present a planned responsibility as if it had already been observed in the system.

When useful, both may be shown separately and compared.

## Relationship with semantic realization

Action Flow can help move from understood work toward candidate realization, but it does not decide architecture by itself.

A possible progression is:

```text
Abstract Action Flow
-> identify semantic responsibilities
-> identify candidate boundaries
-> evaluate boundaries
-> choose contextual realization
-> Systematized Action Flow
```

Boundary evaluation may use criteria such as:

```text
Coherence
    Does the piece represent its purpose correctly?

Cohesion
    Do the elements belong together?

Coupling
    Are the relationships necessary, explicit, and manageable?
```

These are contextual criteria, not mechanical scores.

Delivery forces also affect realization:

```text
Time
Priority
Resources
```

They may justify a simpler or more incremental realization.

They do not authorize semantic contradiction, duplicated authority, or hidden loss of invariants.

## Relationship with VSlices Design stages

Action Flow may evolve naturally across VSlices Design.

### Understanding

Prefer Abstract Action Flows to make work visible without assuming technical structure.

### Contextualizing

Relate flows to:

- Work Lines;
- Work Processes;
- actors;
- roles;
- departments;
- domain contexts;
- existing systems.

### Planning

Use abstract flows plus boundary reasoning to propose a Systematized Action Flow.

This is a realization hypothesis.

### Building

Materialize the proposed responsibilities and update the Systematized Action Flow to reflect the actual realization when useful.

### Return to Understanding

Compare:

```text
understood work
vs
planned realization
vs
implemented behavior
vs
observed runtime behavior
```

Differences become evidence for the next iteration.

## Relationship with Docs Standard

Action Flow is a visual representation.

It does not replace:

- Behavior Documents;
- Context Documents;
- Structure Documents;
- Decision Records;
- Continuity Paths;
- Nexus;
- Support Notes.

A diagram should link to the artifacts that explain the knowledge it shows.

If the diagram requires paragraphs of explanation inside each node, the explanation probably belongs to another artifact.

## Minimal Abstract Action Flow

A useful minimal form needs only:

- a scope;
- ordered actions;
- meaningful conditions;
- meaningful cardinality when needed;
- enough actor information to understand responsibility.

## Minimal Systematized Action Flow

A useful minimal form needs:

- a scope;
- current or proposed state;
- ordered actions;
- human roles where relevant;
- system responsibility lanes;
- meaningful conditions and cardinalities;
- links to concrete implementation evidence when representing an existing system.

## Anti-patterns

Action Flow is misused when:

- every UI gesture is promoted into a business action;
- every business action is forced to correspond to one Feature;
- every lane becomes a deployable service by default;
- file or project structure substitutes semantic responsibility;
- an abstract flow contains technical choices that are not required to understand the work;
- a systematized flow hides important human action or authority;
- a proposed realization is presented as observed;
- a diagram becomes the only source of business rules;
- decomposition continues only to make the diagram look complete.

## Open questions

The following remain deliberately unresolved:

- exact rendering syntax;
- stable visual symbols;
- whether lanes need a normative hierarchy;
- whether Work Line / Process / Flow / Step should become first-class machine-consumable concepts;
- how Tooling should link abstract and systematized actions;
- whether traceability between projections should use stable action identifiers;
- how Action Flow interacts with executable VSIR Flow without conflating documentary work with runtime computation;
- which parts should be renderable by Mermaid and which may require richer Tooling.

These questions should be resolved through use rather than speculative completeness.
