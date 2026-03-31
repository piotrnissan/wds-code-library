# Architectural Principles


## Contract-first architecture

All components are defined through contracts that act as the canonical source of truth.

Contracts describe semantics, structure, behaviour, constraints, and allowed variants independently of any implementation.

All downstream systems (UI implementations, CMS schemas, AI pipelines) must consume and conform to these contracts.


## Implementation-agnostic design

WDS does not prescribe any specific implementation technology (e.g. React, Vue, server-rendered systems).

Contracts are defined in a way that allows multiple implementations to exist in parallel, each mapping the same component definition into a different execution environment.

This ensures portability and prevents coupling the system to a single framework or stack.


## AI-consumable, AI-independent

Contracts are designed to be machine-readable and structured so they can be consumed by AI systems for generation, validation, and transformation.

At the same time, WDS does not depend on any AI pipeline, orchestration layer, or specific model.

AI is a consumer of the system — not a dependency of it.


## Explicit system boundaries

WDS defines clear boundaries between what belongs to the core system and what is external.

The core system includes:
- system model
- component contracts

External systems include:
- UI implementations (e.g. React)
- CMS platforms (e.g. Storyblok)
- AI pipelines and orchestration layers (e.g. MCP)

This separation prevents scope creep and keeps responsibilities well-defined.


## Separation of definition and execution

WDS separates what a component is from how it is executed.

Definition:
- semantics
- structure
- constraints
- behaviour

Execution:
- rendering (UI frameworks)
- content modeling (CMS)
- generation (AI pipelines)

This separation enables independent evolution of contracts and implementations.


## Controlled generation and validation

All outputs generated from contracts (code, CMS schemas, AI-generated artifacts) must be validated against the contract definition.

Generation is not considered authoritative — contracts are.

Human review and automated validation ensure that outputs conform to defined rules and constraints.


## Human-in-the-loop decision model

All AI-assisted outputs (such as contract drafts, constraints, or mappings) must require explicit human validation before becoming part of the canonical system.

AI may assist interpretation and generation, but it is not a source of truth.

No AI-produced artefact enters the system without passing deterministic validation and receiving explicit human approval.


## Composability and extensibility

Components are designed to be composable and reusable across contexts.

Contracts support:
- nesting and composition of components
- extension through additional variants or constraints

The system is structured to allow new adapters, frameworks, and pipelines to be introduced without modifying the core contract model.
