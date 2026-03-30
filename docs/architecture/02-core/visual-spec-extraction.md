# Visual Specification Extraction

## Purpose

The Visual Specification Extraction process defines how visual intent authored in the Design Layer is transformed into a deterministic, machine-readable Visual Specification.

Its purpose is to ensure that visual rules do not remain implicit inside Figma and can instead be formalized as a stable system artefact owned by WDS.

This process is not itself part of component authoring.  
It is the architectural boundary where authored design data becomes system-consumable visual definition.


## Role in the Architecture

The extraction process connects:

- **Design Layer**
  where visual intent is authored

and

- **Visual Specification**
  where visual intent becomes explicit, structured, and machine-readable

This means extraction is the transition point between:
- design-authored representation
- system-owned representation

Without this process, visual definition would remain dependent on interpretation of design files rather than existing as a canonical system artefact.


## Core Principle

Extraction must be deterministic.

Given the same design input, the process must produce the same Visual Specification output.

This is essential because downstream systems must depend on explicit and stable visual definitions rather than:
- manual interpretation
- tool-specific ambiguity
- undocumented design assumptions
- ad hoc implementation choices


## Inputs

The extraction process consumes authored visual information from the Design Layer.

This may include:
- component variants
- component properties
- design tokens
- typography definitions
- color assignments
- spacing definitions
- border and radius usage
- interaction state definitions
- motion intent
- theme-specific visual treatment

The exact form of these inputs depends on the design tooling and authoring conventions, but the extraction process must treat them as source material rather than final system output.


## Outputs

The output of extraction is the **Visual Specification**.

This output must be:

- machine-readable
- explicit
- complete enough for downstream interpretation
- stable across repeated extraction
- independent of live design-tool interpretation at runtime

The extraction output is not a screenshot, not a visual snapshot, and not a design file reference.

It is a structured definition of visual behavior.


## What Extraction Does

At an architectural level, extraction performs the following functions:

### 1. Reads Authored Visual Definitions

It reads the design-authored representation of a component from the Design Layer.

This includes all authored visual dimensions relevant to the component.


### 2. Resolves Visual Axes

It identifies the axes that affect appearance, such as:
- variant
- size
- state
- theme

These axes must be made explicit as part of the output model.


### 3. Resolves Token Usage

It converts authored styling decisions into explicit token-based mappings where applicable.

This includes resolving:
- typography roles
- color roles
- spacing values
- border tokens
- elevation or shadow tokens

No required visual rule should remain dependent on implicit inheritance or tool-only interpretation.


### 4. Normalizes Visual Data

It transforms design-authored information into a stable structure that is independent of:
- Figma-specific authoring patterns
- design tool hierarchy quirks
- presentation-layer inconsistencies
- naming irregularities that are not part of the intended model

This normalization step is what allows WDS to consume design outputs as system data rather than raw tool data.


### 5. Makes State and Theme Behavior Explicit

It formalizes how the visual result changes across:
- interaction states
- themes
- supported visual combinations

Nothing required for interpretation should remain hidden in alternate frames, manual conventions, or undocumented design patterns.


### 6. Produces the Visual Specification Artefact

The final result is a Visual Specification that can be consumed by the System Model and referenced by downstream systems.


## What Extraction Does Not Do

Extraction does not:

- define visual intent
- invent missing design decisions
- interpret business or semantic meaning
- generate framework code
- generate CMS schemas
- define runtime behaviour
- replace governance or validation processes

If source design data is incomplete, inconsistent, or ambiguous, extraction should expose that condition rather than silently filling gaps.


## Architectural Responsibilities

The extraction process is responsible for:

### Formalization
Turning design-authored visual intent into explicit system data.

### Determinism
Ensuring repeatable outputs for the same inputs.

### Normalization
Removing design-tool-specific representation details that are not part of the canonical visual model.

### Boundary Enforcement
Separating design authoring concerns from system consumption concerns.

### Completeness Signalling
Making absence, ambiguity, or unsupported patterns visible rather than hiding them.


## Failure and Ambiguity Handling

The extraction process must not compensate for missing or unclear design information through guesswork.

If the source material is:
- incomplete
- ambiguous
- inconsistent
- structurally invalid for extraction

the process should surface that explicitly.

This is important because silent compensation would turn extraction into an interpretation layer, which would weaken WDS as a deterministic control system.

In other words:
- design may be incomplete
- extraction may fail or warn
- but extraction must not invent canonical truth


## Position Relative to Ownership

Design owns visual intent.

WDS owns the extracted machine-readable representation of that intent.

This distinction matters because it preserves:
- design ownership over visual decisions
- system ownership over formalized artefacts

The extraction pipeline is the controlled handoff between those two responsibilities.


## Relation to Other Layers

### Relation to Design Layer

The Design Layer is the authoring environment.

Extraction reads from it but does not replace it.


### Relation to Visual Specification

The Visual Specification is the output artefact produced by extraction.

It is the formal result of the process.


### Relation to System Model

The System Model consumes the extracted Visual Specification together with semantic definitions from the Planning Layer.

Extraction does not perform model composition.  
It only produces the visual input required for that composition.


### Relation to Governance

Governance may validate whether extraction is:
- complete
- aligned with design intent
- consistent with token policy
- free from drift

But governance does not perform extraction itself.


## Architectural Constraints

The extraction process must satisfy the following constraints:

- **Deterministic**
  The same input must produce the same output.

- **Explicit**
  The output must make visual rules visible and machine-readable.

- **Tool-decoupled**
  The resulting artefact must not require live design-tool interpretation.

- **Non-generative**
  Extraction must not invent missing definitions.

- **Composable**
  The output must be suitable for use by the System Model and downstream execution systems.

- **Extensible**
  The process must support future expansion of states, themes, token families, and visual dimensions without changing its architectural role.


## Conceptual Flow

At a conceptual level, the extraction process follows this progression:

**Design Layer → visual data resolution → normalization → explicit mapping → Visual Specification**

This flow may later be implemented through different technical approaches, but the architectural role remains the same:
to convert authored visual intent into canonical visual system data.


## Key Concepts

- extraction boundary
- deterministic transformation
- visual data normalization
- token resolution
- explicit mapping
- design-to-system handoff
- machine-readable visual output
- non-generative formalization