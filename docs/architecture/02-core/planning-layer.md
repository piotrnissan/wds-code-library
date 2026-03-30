# Planning Layer

## Purpose

The Planning Layer defines the intent of a component before any design or implementation takes place.

It establishes what the component is, why it exists, and what rules govern its usage, independently of visual representation or technical execution.

This layer is responsible for eliminating ambiguity at the earliest stage by providing a clear, structured definition of component behaviour and constraints.

In addition to defining new components, the Planning Layer also supports the reconstruction of existing systems by extracting and formalizing component intent from multiple sources.


## Modes of Operation

The Planning Layer operates in two complementary modes:

- **Forward Definition**
  Used for new components, where intent is defined upfront before design and implementation.
  This includes purpose, behaviour, content structure, constraints, and variants.

- **Reverse Extraction**
  Applied to existing systems, where intent is reconstructed from distributed sources such as design artifacts (e.g. Figma), codebases, CMS models, and real usage.
  This process identifies implicit rules, inconsistencies, and duplication, and formalizes them into a consistent definition.

This makes the Planning Layer both a definition layer and a semantic refactoring layer.


## Inputs

The Planning Layer consumes inputs such as:

- business requirements
- content requirements
- user experience goals and assumptions
- design artifacts (e.g. Figma)
- existing implementations (code, CMS models)
- observed usage patterns

These inputs are often unstructured and may contain inconsistencies.


## Outputs

The Planning Layer produces a structured definition of component intent, including:

- purpose of the component
- behaviour model
- content structure
- constraints
- allowed variants


## Responsibilities

The Planning Layer is responsible for defining:

- **Purpose**
  Why the component exists and what problem it solves.

- **Behaviour**
  What the component does and how it behaves in different contexts.

- **Content Structure**
  What type of content the component accepts and how it is organized.

- **Constraints**
  Rules that define what is allowed or disallowed in usage.

- **Variants**
  The allowed variations of the component (e.g. size, layout, configuration).

It is also responsible for:

- identifying inconsistencies across sources
- normalizing duplicated or conflicting definitions
- making implicit rules explicit


## Non-responsibilities

The Planning Layer does not include:

- visual design or styling
- layout or UI structure
- implementation details
- framework-specific considerations

It does not define how the component looks or how it is built.


## AI Assistance and Human Control

The Planning Layer may be supported by AI systems for:

- extracting signals from multiple sources
- generating structured drafts of planning definitions
- detecting inconsistencies and gaps
- clustering or deduplicating variants

However, AI is not authoritative in defining component intent.

Final decisions about canonical behaviour, constraints, and variants must remain human-driven.

The operating model is human-in-the-loop:
- AI assists in analysis and draft generation
- humans validate, correct, and approve the canonical definition

This ensures that contracts are based on intentional design decisions rather than inferred or inconsistent patterns.


## Key Concepts

The Planning Layer operates on the following core concepts:

- intent
- behaviour model
- constraint model
- variant model


## Relation to Other Layers

The Planning Layer provides input to both the Design Layer (Figma) and the System Model.

It defines the conceptual foundation that is later:

- interpreted visually in Figma
- normalized in the System Model
- formalized in Component Contracts
