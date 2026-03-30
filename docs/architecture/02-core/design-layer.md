# Design Layer (Figma)

## Purpose

The Design Layer represents the visual and interaction interpretation of component intent.

It translates planning definitions into concrete design artifacts, including layout, visual styling, and interaction patterns.

This layer defines how a component looks and behaves from a user experience perspective, but does not act as the authoritative source of component definition.


## Inputs

The Design Layer consumes inputs from the Planning Layer, including:

- component purpose
- behaviour definitions
- content structure
- constraints
- allowed variants

These inputs guide the creation of consistent and intentional design artifacts.


## Outputs

The Design Layer produces design artifacts such as:

- component definitions in Figma
- variants and states
- layout structures
- design tokens (e.g. color, spacing, typography)
- interaction patterns

These artifacts represent the visual and UX realization of the component.

Design artifacts also serve as the source for the Visual Specification, where visual rules are extracted into machine-readable form owned by WDS.


## Responsibilities

The Design Layer is responsible for defining:

- **Visual Representation**
  How the component looks, including layout, styling, and composition.

- **Interaction Design**
  How the component behaves from a user interaction perspective.

- **Design Variants and States**
  Visual and interactive variations of the component.

- **Design Tokens Usage**
  Application of tokens to ensure visual consistency.

It is also responsible for:

- maintaining consistency across components
- ensuring alignment with planning intent
- providing clear visual reference for downstream interpretation


## Non-responsibilities

The Design Layer does not include:

- canonical component definition
- enforceable constraints or validation rules
- implementation logic or framework-specific details
- contract generation

Figma artifacts are not the system of record and are not directly consumed as authoritative input by downstream systems.

Visual rules that WDS depends on must be extracted from the Design Layer into the Visual Specification. The Design Layer is the authoring surface; the Visual Specification is the machine-readable boundary.


## Interpretation vs Definition

The Design Layer is an interpretation layer, not a definition layer.

- Planning defines what the component is and what rules it follows.
- Design interprets that definition into visual and interaction form.

While design artifacts may contain implicit rules, these are not considered canonical until they are formalized in the System Model and Component Contracts.


## Key Concepts

The Design Layer operates on the following core concepts:

- components
- variants
- states
- layout
- design tokens


## Relation to Other Layers

The Design Layer consumes structured intent from the Planning Layer.

It provides visual and interaction input that is extracted into the Visual Specification, which in turn feeds the System Model where definitions are normalized and formalized.

The relationship can be summarized as:

- Planning defines intent
- Design expresses intent visually
- Visual Specification extracts visual rules into machine-readable form
- System Model normalizes semantic and visual definitions into a consistent structure
- Component Contracts formalize the final definition
