# Templates

This folder contains reusable templates for VSlices Docs Standard.

Each template represents a lightweight starting point for preserving a specific kind of knowledge.

## Principle

Use the smallest useful document. Do not create a document because a template exists.

Create a document when future work depends on knowledge that should not be lost.

## Templates

| Template | Use when | 
| --- | --- |
| [Support Note](support-note.md) | Knowledge should not be lost, but it is still too early or lightweight for a formal document. |
| [Domain Vocabulary](domain-vocabulary.md) | Language affects understanding, naming, rules, boundaries, or implementation. |
| [Context Document](context-document.md) | The team needs to preserve where work happens and why it matters. |
| [Process Document](process-document.md) | Responsibilities, coordination, workflows, handoffs, rules, or operational behavior matter. |
| [Use Case Document](use-case-document.md) | A behavior needs explicit meaning, consequence, validations, rules, or expected errors. |
| [Capability Document](capability-document.md) | Several behaviors, workflows, processes, or decisions depend on a stable ability. |
| [Decision Record](decision-record.md) | A choice has meaningful tradeoffs, consequences, risk, or future impact. |
| [Validation Note](validation-note.md) | Evidence confirms, rejects, changes, or improves knowledge future work depends on. |

## Suggested metadata

```yaml
---
id: <type>.<short-name>
type: <document-type>
status: draft
related:
  - <related-artifact-id>
---
```
