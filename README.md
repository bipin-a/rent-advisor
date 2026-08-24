# Rent Advisor

Rent Advisor is a product repository organized as an [Interpretable Context Methodology](https://arxiv.org/abs/2603.16021) software workspace. Product behaviour and technical architecture are owned by the current Project specifications, not by this README.

The reusable form of this workspace model is maintained in the public [`icm-software-workspace-template`](https://github.com/bipin-a/icm-software-workspace-template). Rent Advisor is the configured product instance and remains authoritative for its product intent, repository rules, code, environments, and delivery evidence.

## The workspace model

This repository composes two ICM forms: [`workflows/`](workflows/) is one shared Pipeline, while [`projects/`](projects/CONTEXT.md) is a library of durable Project records that move through it.

A Project is the smallest durable unit that owns a product outcome. It is not synonymous with a conversation, task, issue, pull request, prototype, or architecture spike. One Project may require several of those, repeat Build and validation, and route back when evidence changes the intended result.

Each Project stays at one stable path. Its [`PROJECT.md`](_templates/project/PROJECT.md) records identity, intent, current workflow stage, candidate iteration, delivery shape, architecture holds, and links to canonical artifacts. Shared workflow stages read and update that record; Projects do not copy the workflow or move between stage folders.

A Project folder grows only as its work earns artifacts:

```text
projects/<project-slug>/
├── PROJECT.md
├── specs/
├── prototypes/
├── spikes/
├── decisions/
├── delivery-assessment.md
├── summaries/
└── lessons.md
```

This gives product intent, technical intent, delivery evidence, and decision history one durable custodian across multiple implementation attempts and pull requests.

## Folder boundaries

[`AGENTS.md`](AGENTS.md) is the canonical directory and agent-routing map. These folders separate different kinds of authority:

| Folder | Boundary it protects |
|---|---|
| [`workflows/`](CONTEXT.md) | Defines shared lifecycle transitions once instead of copying a process into every Project. |
| [`projects/`](projects/CONTEXT.md) | Gives each durable product outcome one record and one home for its working artifacts. |
| [`architecture/`](architecture/CONTEXT.md) | Holds cross-Project architecture evidence only when no Project is its natural custodian. |
| [`roadmap/`](roadmap/CONTEXT.md) | Keeps plausible future directions visible without treating them as approved specifications. |
| `_shared/` | Owns configured cross-Project rules and knowledge so Projects link instead of duplicate. |
| `_templates/` | Defines blank, copyable shapes for records and artifacts without mixing factory structure with Project data. |
| [`app/`](app/README.md) | Holds production code once the approved Technical Specification chooses its structure. |

## How work moves

[`CONTEXT.md`](CONTEXT.md) is the canonical lifecycle and task router. It sends durable product work through Spec & Design, delivery assessment, Build, Validate, readiness, Release, and Learn, with a human check at every stage boundary.

Not every conversation becomes a Project. Discussion, diagnosis, and research remain conversational until they change a durable source. Future directions stay in the roadmap until they earn Project status. Narrow architecture uncertainty remains a spike unless it develops its own product outcome, specification, priority, or release.

## Template relationship

Reusable factory improvements may be developed in the template and then deliberately adapted here through a Rent Advisor pull request. There is no automatic synchronization: existing Rent Advisor specifications, configuration, history, and code remain authoritative during every adaptation.
