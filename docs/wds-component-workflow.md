# WDS Component Workflow

## Purpose

The goal of this workflow is to define how a component moves through the WDS system:

Figma → System Model → Component Contract → Implementation → CMS

This repository focuses on the **model and contract layers**, not implementation.

---

## High-level flow

0. Planning (requirements definition)
1. Component is designed in Figma
2. Component is interpreted into a system-level model
3. Component is formalized as a contract
4. Contract is consumed by adapters:
   - implementation layers (e.g. React, Angular)
   - CMS integrations (e.g. Storyblok)
   - AI tooling (generation, validation)
5. Output is generated via AI-assisted pipelines (external to WDS core)

---

## 0. Planning (Requirements Layer)

Before design, components must be defined in terms of requirements.

This includes:
- content structure (e.g. title, media, CTA)
- behavior (e.g. interactions, conditional logic)
- constraints (e.g. required fields, allowed combinations)
- optional features (e.g. video vs image)

This layer is critical for AI workflows:
- Figma alone does not contain sufficient logic
- AI requires explicit requirements to generate correct outputs

Planning + Design together form the full input to the system.

---

## 1. Figma (Design Source)

Figma is the authoring environment for:
- visual structure
- variants
- states
- tokens (colors, spacing, typography)

At this stage:
- components are optimized for design usage
- logic and constraints are implicit

---

## 2. System Model (Internal Representation)

The system model is an abstract representation of the component.

It defines:
- structure (slots, regions)
- content structure (mapped from planning layer)
- properties (inputs)
- variants and states
- constraints (allowed combinations)

This layer:
- is not tied to any framework
- is not tied to Figma structure directly
- exists to normalize components across contexts

---

## 3. Component Contract

The component contract is the **formal definition** of a component.

It includes:
- public API (props / inputs)
- allowed variants and states
- accessibility requirements
- content rules
- behavioral constraints

The contract:
- is framework-agnostic
- is the source of truth for all consumers
- can be used by AI, CMS, and implementation layers

The contract is the boundary between:
- WDS core (definition)
- external systems (AI, CMS, frontend)

It must be explicit and serializable.

---

## Styling vs implementation

WDS may define **styling intent**, but not **framework-specific styling code**.

---

## Adapters (Execution Layer)

Adapters are responsible for translating contracts into specific platforms.

Examples:
- React adapter (component implementation)
- CMS adapter (e.g. Storyblok schema generation)
- AI adapter (prompt + generation logic)

Key principle:
- WDS does not implement components
- WDS defines what should be implemented
- Adapters decide how it is implemented

This enables:
- multi-framework support
- CMS flexibility
- AI-driven generation

---

### What WDS defines (intent)

The contract or model can express semantic styling decisions:

```yaml
textColor: primary
spacing: medium
variant: primary
```

This describes *what something should be*, not *how it is implemented*.

---

### What tokens define (values)

Design tokens provide shared values:

```json
{
  "primary": "#0055FF",
  "spacing-m": "16px"
}
```

Tokens are reusable across all implementations.

---

### What implementation defines (execution)

Implementation libraries (e.g. React, Angular) translate intent into actual code:

```css
.text-primary {
  color: var(--color-primary);
}
```

or:

```html
class="text-blue-600"
```

---

### Key takeaway

WDS defines **meaning (intent)**, not **technology (implementation)**.

This means:
- developers do NOT recreate styling from scratch
- shared UI libraries can exist (e.g. React component libraries)
- those libraries are consumers of the contract, not the source of truth

---

### Why this matters

In a classical design system:
- implementation (often React) becomes the de facto source of truth
- supporting multiple frameworks requires duplicating logic

In WDS:
- the system is defined once (contract)
- multiple implementations can consume it
- the system remains consistent across frameworks, CMS, and AI

---

## 5. CMS / Content Layer

CMS integrations:
- map contract fields to content fields
- enforce constraints defined in the contract

Example:
- Button contract → label, icon, URL
- CMS → fields with validation based on contract

---

## AI & MCP (External Pipeline)

AI workflows (e.g. MCP + Claude) operate outside of WDS core.

They:
- consume contracts
- generate implementations
- orchestrate integrations (CMS, deployment)

Important constraint:

WDS must not depend on MCP or any specific AI tooling.

Instead:
- WDS provides structured input (contracts)
- AI pipelines consume that input

This prevents:
- vendor lock-in
- opaque "black box" behavior

---

## Governance (Required)

To ensure consistency across AI-driven workflows:

- contracts must be versioned
- components must be approved before use
- generation pipelines must be controlled
- outputs should be validated against contracts

Without governance:
- inconsistent implementations will emerge
- WDS can be bypassed by ad-hoc AI usage

---

## Key principles

- Contracts define behavior, not implementation
- Figma is not the source of truth for logic
- Implementation is replaceable, contracts are not
- The system must be framework-agnostic
- AI should consume contracts, not raw design

---

## Open questions (to be defined)

- What is the exact format of the system model?
- What is the serialization format of contracts?
- How much logic belongs in the contract vs adapters?
- How do we enforce constraints in CMS and AI layers?