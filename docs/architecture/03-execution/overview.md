# Execution Layers

Execution Layers define how WDS Component Contracts are translated into runtime-specific artefacts used by downstream systems.

WDS does not execute components. It defines them.

Execution happens in external systems such as frontend frameworks, CMS platforms, and AI-driven pipelines. Execution Layers provide the boundary between the canonical definition (WDS) and these runtime environments.

## Role of Execution Layers

Execution Layers are responsible for translating Component Contracts into forms that can be consumed by specific runtimes.

They exist to:
- materialize component definitions in execution environments
- adapt canonical structures to platform-specific formats
- enforce contract constraints at runtime boundaries
- expose incompatibilities between contracts and execution targets

Execution Layers do not define components and do not introduce new sources of truth.

## Execution Adapters

Execution is performed through adapters.

An adapter is a bounded, execution-specific translator that:
- consumes a Component Contract
- applies execution-specific mapping
- produces runtime artefacts required by a target system

Adapters are replaceable and independent. Multiple adapters can consume the same Component Contract without modifying it.

## Adapter Input

The canonical input to any adapter is the Component Contract.

This may include:
- semantic definition
- structural rules
- variants and states
- composition constraints
- accessibility requirements
- behavioural expectations
- content constraints

Adapters may also consume execution-specific configuration such as:
- mapping rules
- naming conventions
- platform capability profiles
- environment policies

These inputs are local to the adapter and must not be treated as canonical definitions.

## Adapter Output

Adapters produce runtime artefacts required by downstream systems.

Depending on the target environment, this may include:
- frontend component scaffolds and schemas
- CMS content models and validation rules
- structured definitions for dynamic or automated systems
- runtime metadata and configuration
- testing or validation artefacts

Adapter outputs are derived artefacts. They are not sources of truth.

## Types of Execution Adapters

Execution Adapters can be grouped into three primary categories.

### UI Adapters

UI Adapters translate Component Contracts into artefacts used by frontend runtimes.

They produce structures such as:
- component interfaces
- render schemas
- variant mappings
- runtime validation logic

They do not define styling implementation or visual design. Those remain outside WDS.

### CMS Adapters

CMS Adapters translate Component Contracts into editorial and content structures.

They produce:
- content type definitions
- field schemas
- validation rules
- composition constraints for editors

They ensure that content authored in CMS environments remains compliant with the Component Contract.

### AI Adapters

AI Adapters translate Component Contracts into structured inputs for AI-driven systems.

They define:
- constraints for generation
- structured schemas for inputs and outputs
- rules for composition and validation

They do not define component behaviour independently. They enforce the behaviour defined in the Component Contract.

## Responsibility Boundaries

Execution Layers may:
- translate contracts into runtime-specific representations
- apply platform-specific conventions
- validate compatibility with target systems
- report unsupported capabilities

Execution Layers must not:
- redefine component meaning
- introduce new canonical rules
- override required constraints from the contract
- hide incompatibilities between contract and runtime
- become a source of truth

## Architectural Position

Execution Layers sit outside the WDS core.

WDS owns definition.
Adapters own translation.
External systems own execution.

This separation allows a single Component Contract to be consumed by multiple systems without coupling WDS to any specific framework, CMS, or AI implementation.