# Purpose and Scope

## Purpose

WDS Code Library defines a contract-first system that connects design, development, AI, and CMS through a shared, structured model of components.

The purpose of WDS is to provide a single, consistent source of truth for component semantics, behaviour, and constraints, independent of any specific implementation or technology stack.

WDS does not aim to:
- provide a UI component library (e.g. React components)
- define CMS schemas or structures
- implement AI pipelines or orchestration layers

Instead, WDS exists to:
- define component meaning (intent), not implementation
- produce structured contracts that can be consumed by multiple systems
- enable AI-driven workflows by providing deterministic, machine-readable input
- enforce consistency across implementations through shared definitions

WDS sits between design and execution:
- upstream: it consumes planning inputs and design artifacts (e.g. Figma)
- downstream: it provides contracts to adapters, implementations, and AI pipelines

By separating definition (contracts) from execution (implementations and pipelines), WDS enables:
- multi-framework support (React, others)
- multi-CMS integration (e.g. Storyblok)
- AI-assisted generation with controlled outputs
- long-term scalability without coupling to specific technologies

This makes WDS a control layer in the ecosystem — not a rendering layer, and not an execution engine.

## System Scope

### What WDS Core Owns

WDS Core is responsible for defining, storing, and validating the canonical representation of components through contracts.

The primary deliverables of WDS Core are:

- Component Contracts
  - structured, machine-readable artifacts (e.g. JSON, YAML, or equivalent)
  - define component semantics, structure, behaviour, constraints, and variants
  - act as the single source of truth for all downstream systems

In addition to contracts, WDS Core includes system-level capabilities:

- System Model
  - internal representation used to construct contracts
  - not a primary deliverable, but part of the authoring and transformation process

- Contract Definition Logic
  - rules that define how contracts are structured and interpreted

- Contract Validation
  - validation mechanisms (rules, checks, tooling) used to ensure that outputs conform to contracts

- Contract Versioning
  - versioned contract artifacts (e.g. versioned files or schemas)
  - enables controlled evolution and backward compatibility

In practice, WDS Core is a repository of contracts plus the logic required to define, validate, and evolve them.


### What WDS Core Does Not Own

WDS explicitly does not own any execution layer or downstream system.

This includes:

- UI Implementations
  - e.g. React, Vue, or other frameworks
  - rendering logic and styling implementation

- CMS Schemas and Content Models
  - e.g. Storyblok or other CMS platforms
  - content storage, editorial workflows, and CMS-specific structures

- AI Pipelines and Orchestration
  - e.g. MCP or similar systems
  - prompt execution, model selection, and pipeline logic

- Build and Deployment Systems
  - compilation, bundling, hosting, and runtime environments

- Design Tools as Systems of Record
  - e.g. Figma is not the system of record for component definitions
  - design artifacts represent visual intent, not enforceable system rules

Figma remains the authoritative source for visual design intent, but not for executable or enforceable definitions.

Contracts formalize and extend what is expressed in design into a system that can be consumed and validated.


### Where WDS Fits in the Ecosystem

WDS acts as a central contract layer positioned between design inputs and execution systems.

Upstream:

- Planning
  - defines requirements, content structure, behaviour, and constraints

- Design (Figma)
  - defines visual appearance and interaction intent
  - provides input into the component definition process

Core:

- WDS
  - transforms planning and design inputs into structured contracts
  - maintains contracts as the source of truth

Downstream:

- UI Implementations (via adapters)
  - consume contracts to render components

- CMS Platforms (via adapters)
  - map contracts to content schemas and structures

- AI Pipelines
  - use contracts as structured input for generation and transformation

- Build and Deploy Systems
  - execute outputs generated from contracts

WDS does not integrate or orchestrate these systems directly.

Instead, it provides a stable, shared contract layer that all systems consume.

This positions WDS as a control layer that defines and enforces consistency, while execution remains external.
