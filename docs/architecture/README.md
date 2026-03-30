# WDS Architecture

WDS defines a contract-first system that provides a single, structured source of truth for component semantics, behaviour, and constraints.

WDS is a **control layer** — it defines and enforces the rules that all downstream systems must follow.

WDS is **not** a UI library, a CMS, or an AI pipeline. It sits between design and execution, producing structured contracts that multiple systems consume independently.

WDS defines both:
- **semantic definition** (what a component is and how it behaves)
- **visual definition** (how a component looks across all supported dimensions)

Both must exist as explicit, machine-readable artefacts within the system.


## High-Level Flow

```
Planning → Design Layer → Visual Specification → System Model → Component Contracts → Adapters / Execution
```

The transition between Design Layer and Visual Specification is handled by a deterministic **extraction process**, which formalizes design-authored visual intent into a system-owned representation.

Figma is used for authoring visual intent.  
WDS owns the extracted, machine-readable representation of that intent.


## Documentation

### System

- [Purpose and Scope](01-system/purpose-and-scope.md) — why WDS exists and system boundaries
- [Architectural Principles](01-system/architectural-principles.md) — the core rules that shape the architecture
- [Architectural Overview](01-system/architectural-overview.md) — layered structure, end-to-end flow, and system dynamics

### Core Layers

- [Planning Layer](02-core/planning-layer.md) — defining component intent before design or implementation
- [Design Layer](02-core/design-layer.md) — visual and interaction authoring via Figma
- [Visual Specification](02-core/visual-specification.md) — machine-readable visual definition owned by WDS
- [Visual Specification Extraction](02-core/visual-spec-extraction.md) — deterministic transformation from design to system artefact
- [System Model](02-core/system-model.md) — internal normalization and canonicalization of semantic and visual definitions
- [Component Contracts](02-core/component-contracts.md) — the canonical, machine-readable output of WDS

### Execution

- [Execution Layers](03-execution/overview.md) — React, CMS, and AI adapters
- [External Pipeline](03-execution/external-pipeline.md) — orchestration, implementation pipelines, and build/deploy concerns

### Governance

- [Contract Enforcement](04-governance/contract-enforcement.md) — validation, review, and output conformance
- [Styling Governance](04-governance/styling.md) — ownership, consistency, validation, and drift control for visual definitions
- [Versioning](04-governance/versioning.md) — governance, versioning, and change management

### Reference

- [End-to-End Example](05-reference/end-to-end-example.md) — a complete walkthrough
- [Architectural Decisions](05-reference/architectural-decisions.md) — key decisions and rationale
- [Open Questions](05-reference/open-questions.md) — unresolved topics