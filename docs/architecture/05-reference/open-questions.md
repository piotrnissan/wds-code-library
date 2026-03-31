# Open Questions

## Q-001: Visual Specification Schema

### Problem
The exact machine-readable schema for Visual Specification is not yet defined.

### Why it matters
Without a formal schema:
- extraction cannot be implemented consistently
- downstream systems cannot rely on stable structure
- validation becomes difficult

### Possible directions
- JSON-based schema with strict typing
- layered schema (tokens → mappings → resolved properties)
- minimal schema first, extended over time

### Status
open


## Q-002: Extraction Implementation Strategy

### Problem
The mechanism for extracting Visual Specification from Figma is not yet defined.

### Why it matters
Extraction is the bridge between design and system. Its implementation affects:
- reliability
- maintainability
- adoption by design teams

### Possible directions
- Figma plugin
- Figma API-based pipeline
- hybrid approach (plugin + post-processing)
- AI-assisted extraction with deterministic validation

### Status
open


## Q-003: Source of Truth Boundaries

### Problem
Potential divergence between Design Layer (Figma) and Visual Specification.

### Why it matters
Unclear ownership could lead to:
- conflicting definitions
- drift between design and system
- inconsistent execution

### Possible directions
- Visual Spec as authoritative system output
- validation rules enforcing alignment
- governance workflows for reconciliation

### Status
open


## Q-004: Token Governance Model

### Problem
Ownership and lifecycle of design tokens are not clearly defined.

### Why it matters
Tokens are foundational for visual consistency and must be managed across:
- design
- WDS
- execution systems

### Possible directions
- design-owned tokens with WDS validation
- shared ownership model
- WDS-controlled token registry

### Status
open


## Q-005: Versioning Strategy for Visual Specification

### Problem
It is unclear how Visual Specification should be versioned relative to Component Contracts.

### Why it matters
Versioning affects:
- backward compatibility
- rollout of visual changes
- synchronization across systems

### Possible directions
- independent versioning of Visual Spec and Contracts
- shared versioning per component
- semantic versioning based on impact

### Status
open


## Q-006: CMS Mapping Ownership

### Problem
Responsibility for mapping WDS components to CMS structures is not clearly defined.

### Why it matters
Incorrect ownership could lead to:
- duplication of logic
- inconsistent CMS implementations
- tight coupling between WDS and specific platforms

### Possible directions
- mapping handled entirely in adapters
- partial mapping defined in WDS
- hybrid approach

### Status
open


## Q-007: AI Consumption Model

### Problem
How AI systems should consume WDS outputs is not fully defined.

### Why it matters
AI is a key consumer of WDS, and unclear integration may result in:
- inconsistent outputs
- over-reliance on prompts instead of structure
- loss of determinism

### Possible directions
- structured schema consumption
- prompt templates generated from contracts
- hybrid model combining schema and prompts

### Status
open


## Schema & Structure

## Q-008: Formal Schema for Component Contracts

### Problem
Component Contracts lack a formal, machine-readable schema definition.

### Why it matters
Without formal schema:
- validation cannot be automated
- code generation tools cannot be built
- downstream systems have no guaranteed contract

### Possible directions
- JSON Schema
- TypeScript type definitions with validation
- Protobuf
- Custom DSL

### Status
open


## Q-009: Formal Schema for Visual Specification

### Problem
Visual Specification lacks a formal, machine-readable schema definition.

### Why it matters
Without formal schema:
- extraction logic cannot be validated
- adapters cannot reliably consume visual data
- transformation consistency cannot be guaranteed

### Possible directions
- token-based schema (name → resolved value)
- layered schema (design tokens → mappings → resolved properties)
- JSON-based with strict typing
- minimal schema first, extended over time

### Status
open


## Q-010: Machine-Readable Constraint Representation

### Problem
Constraints are expressed in natural language within contracts; no machine-readable format exists (AD-010 documents this as future concern).

### Why it matters
Natural language constraints prevent:
- automated validation
- conflict detection
- deterministic constraint resolution

### Possible directions
- constraint expression language (imperative or declarative)
- constraint graph with resolution logic
- rules engine integrated into System Model

### Status
future


## Artefact Relationships

## Q-011: Component Contract and Visual Specification Versioning

### Problem
Unclear whether Component Contracts and Visual Specifications should be versioned together or independently (AD-009 establishes independent versioning; this question explores implementation).

### Why it matters
Versioning strategy affects:
- backward compatibility maintenance
- deployment coordination
- change rollout complexity

### Possible directions
- independent semantic versioning for each
- coupled versioning (same version for both in a release)
- component-level versioning with sub-versions for visual/semantic changes
- timestamp-based or content-hash-based linking

### Status
open


## Q-012: Handling Contract-Specification Drift

### Problem
Visual Specification and Component Contract may diverge if not synchronized intentionally (AD-009 specifies explicit review required; this explores detection and resolution).

### Why it matters
Drift can cause:
- incorrect component rendering
- confusing developer experience
- silent failures

### Possible directions
- automated validation step detecting misalignment
- migration tooling suggesting required Contract updates
- governance workflow flagging outdated references

### Status
open


## System Boundaries

## Q-013: Planning Layer Responsibility Boundaries

### Problem
Exact responsibility boundary between Planning Layer and System Model is not formalized.

### Why it matters
Unclear boundaries may lead to:
- duplication of constraint definitions
- unexpected dependencies
- role confusion during architecture evolution

### Possible directions
- Planning defines intent and rules; System Model applies them to visual definitions
- Planning defines only high-level concepts; System Model handles all details
- clear separation with explicit handoff criteria

### Status
open


## Q-014: Normalization vs. Resolution in System Model

### Problem
Whether System Model should only normalize inputs or also resolve conflicts is undefined.

### Why it matters
Scope affects:
- when conflicts are detected
- where transformation logic lives
- error handling strategy

### Possible directions
- System Model normalizes only (no conflict resolution; conflicts bubble up)
- System Model resolves conflicts with predefined rules
- hybrid: normalizes all inputs, escalates unresolvable conflicts

### Status
open


## Composition Model

## Q-015: Component Composition and Slot Definition

### Problem
How components compose and how slots are defined and constrained is not yet specified.

### Why it matters
Composition affects:
- contract complexity
- variant explosion
- system scalability

### Possible directions
- slot constraints expressed as contract references (must accept component X)
- content model (slot accepts text, components, mixed)
- variant constraints on composed components

### Status
open


## Q-016: Contract Cross-References

### Problem
How Component Contracts reference other components (inheritance, composition, variants) is not formalized.

### Why it matters
Cross-references affect:
- circular dependency potential
- versioning complexity
- system navigation

### Possible directions
- explicit component dependency graph
- versioned references (contract A v2.0 requires component B v1.5+)
- lazy resolution (references resolved at runtime in adapters)

### Status
open


## Ownership & Lifecycle

## Q-017: Layer Ownership Model

### Problem
Clear ownership of each architectural layer (Planning, Design, System Model, Contracts, Adapters) is not assigned.

### Why it matters
Unclear ownership leads to:
- disputed decisions
- delayed issue resolution
- accountability gaps

### Possible directions
- product/design owns Planning; designers own Design; architect owns System Model; engineers own Adapters
- cross-functional ownership with clear escalation paths
- domain-based ownership per component family

### Status
open


## Q-018: Component Lifecycle and States

### Problem
Lifecycle states (draft, approved, stable, deprecated, removed) and transitions are not defined.

### Why it matters
Lifecycle clarity affects:
- when adapters can consume a contract
- rollout planning
- breaking change management

### Possible directions
- draft → approved → stable → deprecated → removed
- risk-based approval (low-risk changes auto-approve)
- fast-track for bug fixes vs. feature additions

### Status
open


## Q-019: Conflict Resolution Authority

### Problem
When Planning Layer and Visual Specification conflict (e.g., semantic rules vs. visual constraints), who decides and how?

### Why it matters
Unclear authority may lead to:
- stalled decisions
- system deadlock
- inconsistent resolution patterns

### Possible directions
- System Model has authority (both inputs adapt)
- Planning has authority (visual spec updates)
- Visual has authority (planning contracts)
- human committee review for disputes

### Status
open