# External Pipeline

The External Pipeline defines how Component Contracts move through orchestration, transformation, validation, and delivery flows outside the WDS core.

WDS itself does not execute these flows. It produces the canonical outputs that external systems consume.

The External Pipeline exists to coordinate how contracts are interpreted, transformed, validated, and materialized by downstream systems such as UI runtimes, CMS platforms, and AI-driven workflows.

## AI / MCP Orchestration

AI and orchestration systems may use Component Contracts as structured inputs for generation, transformation, validation, and decision-support workflows.

In this context, orchestration refers to the external coordination layer that determines:
- which contracts are used
- which tools or models are invoked
- how execution steps are sequenced
- where validation happens
- where human approval is required

MCP or similar orchestration mechanisms may provide the technical interface between contracts, tools, models, and downstream systems. These mechanisms are part of the execution environment, not part of WDS itself.

WDS does not define prompts, model routing, tool chains, or execution logic. It provides the canonical component definitions that orchestration systems can consume in a controlled and machine-readable form.

This separation is critical. It allows multiple AI systems, orchestration frameworks, or toolchains to operate from the same source of truth without turning orchestration logic into component definition.

## Implementation Pipelines

Implementation Pipelines are external flows that materialize Component Contracts into runtime-specific artefacts.

These pipelines may include:
- adapter execution
- schema generation
- code generation
- CMS model synchronization
- validation against runtime constraints
- packaging of generated artefacts

Different targets may require different implementation pipelines, but each pipeline must treat the Component Contract as its canonical source.

Implementation Pipelines may apply target-specific conventions, templates, and mappings. However, they must not redefine component meaning, introduce alternative rules, or silently change contract constraints.

If a target system cannot support part of a contract, the pipeline must expose that limitation explicitly rather than compensating for it through undocumented behaviour.

## Build and Deploy

Build and deployment activities belong to downstream delivery environments.

They may consume artefacts produced by implementation pipelines, but they are not part of WDS and are not owned by the WDS core architecture.

Examples include:
- frontend application builds
- CMS deployment workflows
- publishing or synchronization jobs
- AI workflow deployment and runtime configuration

WDS does not build products and does not deploy runtimes. It defines the canonical component outputs that downstream systems use during build and deployment.

This distinction ensures that WDS remains a definition system rather than becoming coupled to delivery infrastructure or operational tooling.

## Architectural Boundary

The External Pipeline sits entirely outside the WDS core.

WDS is responsible for definition.
Execution Adapters are responsible for translation.
External Pipelines are responsible for orchestration and delivery coordination.
Downstream systems are responsible for runtime execution.

This model preserves a clear boundary between canonical definition and operational execution, allowing the same Component Contracts to support multiple pipelines, runtimes, and orchestration strategies without changing the core architecture.