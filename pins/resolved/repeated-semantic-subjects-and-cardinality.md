# Repeated semantic subjects and cardinality

## Resolution status

Resolved.

The original research question was:

> Does Docs Standard need to model repeated semantic subjects inside a Document, in addition to questions and answers?

The cardinality pressure that motivated this pin is now satisfied without introducing a separate semantic-subject primitive.

## Reconstructible trajectory

### Initial hypothesis

Early Domain Vocabulary and Consistency evidence suggested:

~~~text
one semantic question
    -> N semantic subjects
        -> the same subordinate questions for each subject
~~~

This made a distinct internal semantic-subject abstraction appear likely.

### Stronger recursive pressure

Domain Vocabulary then introduced nested repetition:

~~~text
Vocabulary
    -> N terms
        -> N associated properties per term
~~~

The important requirement was therefore not merely a collection of named subjects. Tooling needed to preserve independent progressive authoring state recursively.

### Revision

Further analysis produced a smaller composable model:

~~~text
QuestionDefinition
    -> one | many AnswerInstances
        -> child QuestionOccurrences scoped to each AnswerInstance
            -> one | many child AnswerInstances
            -> ...
~~~

Docs Standard now owns the normative cardinality vocabulary:

~~~yaml
cardinality: many
~~~

with omitted cardinality meaning `one`.

Domain Vocabulary provides executable witnesses through:

- `terms`;
- `associated-properties`;
- `confusable-terms`.

### Executable evidence

The Tooling experiment established that the recursive model can:

- create several AnswerInstances for one `many` QuestionOccurrence;
- preserve distinct technical identity even when answer text is equal;
- reconstruct repeated AnswerInstances from the materialized Document;
- keep a `many` occurrence available for further answers;
- scope child QuestionOccurrences independently through one concrete AnswerInstance;
- carry that scope through deeper descendants;
- create nested repeated AnswerInstances under an outer AnswerInstance;
- keep nested repetition under different outer AnswerInstances independent.

The resulting shape is executable:

~~~text
terms [many]
├─ Account
│  └─ associated-properties [many]
│     ├─ Rut
│     └─ Status
└─ Service
   └─ associated-properties [many]
      └─ Endpoint
~~~

This demonstrates the required recursive N × M composition without a Domain Vocabulary-specific mechanism.

## Resolution

For cardinality and progressive authoring, Docs Standard does **not currently require a separate semantic-subject primitive**.

The promoted minimum is:

~~~text
QuestionDefinition
-> cardinality: one | many
-> AnswerInstance
-> scoped child QuestionOccurrences
-> recursively repeated AnswerInstances
~~~

AnswerInstance technical identity is sufficient for reconstruction and authoring scope.

This does not prove that semantic subject identity can never become useful. If future evidence requires stable references, continuity across reordering, cross-Document targeting, Nexus promotion, or other semantics that technical AnswerInstance identity cannot honestly carry, that should open a more precise research question rather than reopening cardinality by default.

## Normative consequence

Docs Standard owns question cardinality and recursive question vocabulary.

Template Standard owns how repeated and scoped AnswerInstances are materialized and reconstructed.

Tooling owns selection, authoring, reconstruction, and mutation mechanisms.

No special `Term`, `Subject`, `Row`, `Entity`, or equivalent primitive is introduced merely to support cardinality.

## Historical distinctions retained

The original pin distinguished:

~~~text
question cardinality
subject cardinality
answer cardinality
~~~

That distinction was useful during exploration, but the executable evidence showed that the cardinality problem can currently be represented through recursive QuestionOccurrence / AnswerInstance alternation.

The original semantic-subject hypothesis remains historical evidence rather than current normative authority.
