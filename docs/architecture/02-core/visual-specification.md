# Visual Specification

## Purpose

The Visual Specification is the machine-readable visual definition of a component, owned by WDS.

It formalizes all visual rules that affect how a component appears, ensuring that no visual decision required by the system exists only implicitly in the Design Layer (Figma).

The Visual Specification is produced through a deterministic extraction process from the Design Layer.

Design defines visual intent.  
WDS defines the exported, machine-readable representation of that intent.

The Visual Specification exists as a deterministic system artefact that can be consumed by the System Model and downstream execution systems.


## Source of Truth and Authoring Model

Visual decisions are authored in the Design Layer (Figma), which serves as the primary authoring environment.

The Visual Specification is produced from this source through a deterministic extraction process defined within WDS.

- **Figma** is the source of visual intent
- **Visual Specification** is the source of system-consumable visual definition

Downstream systems must not rely on Figma as a runtime dependency.  
They consume the Visual Specification as the canonical visual input.

Extraction may be:
- automated
- semi-automated
- manual

However, the resulting Visual Specification must always be:
- explicit
- complete
- deterministic


## What the Visual Specification Contains

The Visual Specification defines the visual behavior of a component across all supported dimensions.

It is not a direct representation of design files.  
It is a normalized, system-oriented model of visual behavior.

It includes:

### 1. Visual Axes

Dimensions that affect appearance, such as:
- variants (e.g. primary, secondary)
- sizes (e.g. sm, md, lg)
- states (e.g. default, hover, focus, active, disabled)
- themes (e.g. light, dark, brand-specific)

These axes define the space over which visual rules are applied.


### 2. Token Mapping

Explicit mapping between semantic roles and design tokens, including:
- color assignments
- typography mappings
- spacing values
- border definitions
- elevation or shadow tokens

Mappings must be resolved and not rely on implicit inheritance from design tools.


### 3. Visual Properties

Concrete visual definitions derived from token mapping, such as:
- text styles (font, size, weight, line height)
- background and foreground colors
- spacing (padding, margin, gap)
- borders (radius, width, style)
- layout alignment constraints

These define how the component is rendered visually.


### 4. State and Theme Resolution

Explicit definitions of how visual properties change across:
- interaction states (hover, focus, active, disabled)
- themes (light, dark, brand variations)

No state-dependent behavior may remain implicit.

All supported combinations must be resolvable without interpretation.


### 5. Interaction Styling

Visual aspects of interaction, including:
- focus indicators
- hover treatments
- active feedback
- disabled states

This includes only visual outcomes, not event handling logic.


### 6. Motion Definition

Where applicable, motion-related rules such as:
- transition properties
- durations
- easing curves

Motion is defined as visual behavior, not implementation code.


### 7. Visual Constraints

Rules that restrict valid visual combinations or enforce consistency, such as:
- disallowed variant + state combinations
- required contrast levels
- minimum spacing or sizing rules

These constraints ensure correctness and consistency across implementations.


## Minimal Structural Shape

At an architectural level, a Visual Specification defines:

- component identity
- visual axes (variants, sizes, states, themes)
- token mappings
- resolved visual properties
- state and theme mappings
- interaction and motion rules
- visual constraints

The exact serialization format (e.g. JSON schema) is defined separately, but the structure must support deterministic resolution of all visual outcomes.


## Resolution Model

The Visual Specification must support deterministic resolution of visual output.

Given:
- a component
- a set of visual axes (e.g. variant, size, state, theme)

the system must be able to resolve:
- the complete set of visual properties
- without ambiguity
- without relying on external tools
- without requiring implicit inheritance

This requirement ensures that:
- execution layers can render consistently
- AI systems can generate correct output
- CMS integrations can apply styling deterministically


## Responsibilities

The Visual Specification is responsible for:

### Visual Formalization
Converting design-authored visual intent into a machine-readable system artefact.

### Completeness
Ensuring no required visual rule exists only in Figma.

### Determinism
Providing unambiguous visual definitions that produce consistent results across all consumers.

### Platform Independence
Defining visual rules without reference to any specific implementation technology (CSS, React, etc.).

### Stability for Downstream Systems
Serving as a reliable input for the System Model and execution layers.


## Non-responsibilities

The Visual Specification does not include:

- design authoring or editing (Design Layer)
- semantic component intent or business rules (Planning Layer)
- structural or layout composition of the component tree (System Model)
- runtime implementation (CSS, JS, frameworks)
- CMS or platform-specific mappings
- governance processes (ownership, validation, drift control)

It is strictly the boundary where visual design becomes system-readable data.


## Relation to Other Layers

The Visual Specification sits between the Design Layer and the System Model.

- **Design Layer**
  Defines visual intent and authoring through Figma

- **Visual Specification**
  Extracts and formalizes that intent into machine-readable form

- **System Model**
  Consumes both:
  - semantic definitions from Planning
  - visual definitions from Visual Specification

  and normalizes them into a unified internal representation

- **Component Contracts**
  Represent the canonical output of WDS and may reference visual definitions, but do not need to contain all raw visual data

- **Styling Governance**
  Ensures correctness, consistency, and alignment between Design, Visual Specification, and Execution, but does not define visual rules


## Architectural Constraints

The Visual Specification must satisfy the following constraints:

- **No Implicit Visual Logic**
  All visual behavior required by the system must be explicitly defined.

- **No Runtime Dependency on Design Tools**
  Downstream systems must not depend on Figma for interpretation.

- **Deterministic Resolution**
  Given the same input axes (variant, state, theme), the same visual output must always be produced.

- **Separation of Concerns**
  Visual definition must remain independent from semantics, structure, and execution.

- **Extensibility**
  The model must support extension (e.g. new states, themes, tokens) without breaking existing definitions.


## Key Concepts

- visual specification
- machine-readable visual definition
- token mapping
- visual axes
- state and theme resolution
- interaction styling
- motion definition
- extraction boundary
- design-to-system formalization