# Key Open Questions

These are the most important decisions that need alignment before implementation.
Each question includes a short explanation and a suggested direction to guide discussion.

---

## 2. Extraction Strategy from Figma

How do we extract Visual Specification from Figma?

Options (simple explanation):

- Figma plugin  
  A custom plugin inside Figma that allows designers to annotate components and export structured data.  
  Pros: designer-friendly, integrated workflow  
  Cons: requires building and maintaining a plugin  

- API-based pipeline  
  A backend script or service that pulls data from Figma via API and transforms it into Visual Specification.  
  Pros: centralized, easier to control and automate  
  Cons: less visibility for designers, requires mapping logic  

- Hybrid approach  
  Combine both: plugin for metadata/annotations + API pipeline for extraction and processing.  
  Pros: best balance between usability and control  
  Cons: more complex setup  

- AI-first approach:
  Use AI as the primary interpreter of Figma data (structure, naming, variants, relationships) to generate a first draft of the Visual Specification.

  - AI processes raw Figma data (via API and/or plugin-exported metadata)
  - AI proposes structured output (variants, states, elements, mappings)
  - Human reviews and corrects where needed
  - Deterministic validation enforces schema and consistency before acceptance

  Pros:
    + Faster authoring and iteration
    + Handles ambiguity in design data
    + Scales across many components

  Cons:
    − Requires strong validation layer
    − Needs clear human review workflow
    − Potential inconsistency without guardrails

Suggested direction:
AI-first hybrid approach (AI interpretation + human review + deterministic validation), supported by API pipeline and optional plugin for metadata input.

---

## 3. Source of Truth Boundary

What is authoritative in case of conflict?

Options:
- Design (Figma) as source of truth
- Visual Specification as system truth
- Component Contract as final truth

Pros / Cons:

- Figma  
  + Familiar for designers  
  − Not structured enough for system-level validation  

- Visual Specification  
  + Structured, close to design  
  − Derived artefact, may drift  

- Component Contract  
  + Fully structured and validated  
  + Used by all downstream systems  
  − Less visible to designers  

Suggested direction:
Component Contract as the ultimate source of truth, with Visual Specification as an intermediate system artefact and Figma as the authoring layer.

---

## 4. Contract & Visual Spec Versioning

Should they be versioned:
- independently
- together
- or linked

Note:
This is likely an internal technical decision (may involve ISIT), not a strategic alignment topic.

Suggested direction:
Independent versioning with explicit linking (as already outlined in architecture).

---

## 5. Constraint Representation

How do we represent rules?

Today:
- mostly natural language

Future:
- machine-readable constraints

Example:
Instead of:
- "Icon-only button must have aria-label"

We define:
- condition: variant = icon-only  
- requirement: aria-label is required  

Why it matters:
- enables validation
- enables AI consumption
- removes ambiguity

Suggested direction:
Move towards machine-readable constraints (rule-based system), while allowing natural language during early stages.

---

## 6. CMS Mapping Ownership

What does "CMS mapping" mean?

It is the translation of Component Contracts into CMS structures, e.g.:
- fields
- content types
- configuration rules

Question:
Where should this logic live?

Options:
- fully in adapters (CMS-specific layer)
- partially defined in WDS
- hybrid

Suggested direction:
Keep CMS mapping primarily in adapters to avoid coupling WDS to specific platforms, with minimal shared definitions if needed.

---

## 7. Ownership Model

Who owns each layer?

Suggested model:

- Planning → Product / Design (intent, behaviour)
- Design (Figma) → Designers (visual definition)
- System Model → Architecture / Design Tech (normalization, rules)
- Component Contracts → Shared ownership (Design + Engineering)
- Adapters → Engineering teams (platform-specific implementation)

Goal:
Clear responsibility per layer with minimal overlap.

---

## Goal

These questions are not blockers yet — but they define:
- how fast we can move
- how scalable the system becomes

We need alignment on direction, not perfect answers.