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