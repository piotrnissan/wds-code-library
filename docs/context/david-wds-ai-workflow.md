# WDS Code Library — AI Workflow (David Proposal)

## Status

External proposal / reference

This document captures David’s proposed AI-driven workflow around WDS Code Library.
It is NOT the definition of WDS architecture, but an important input for it.

---

## 1. Overview

David’s proposal defines an AI-assisted pipeline connecting:

- Design (Figma)
- Code (React / frontend)
- CMS (Storyblok)
- Deployment (Vercel)

Core idea:

Move from static design handoff → to automated, component-driven workflow powered by AI.

---

## 2. Key Workflows

### 2.1 Figma → Code Library

Flow:

Figma (WDS Design Library) → MCP → AI (Claude) → WDS Code Library

Goal:

Generate reusable frontend components directly from design.

Output:

- Typed React components
- Token-based styling (CSS variables)
- Documentation site (Next.js)
- GitHub repository

Stack:

- React + TypeScript
- CSS Modules
- Next.js (docs)
- Vercel (hosting)

Example scale (from POC):

- 5 atoms
- 24 components
- 99 design tokens
- 26 documentation pages

---

### 2.2 Figma → Frontend Prototypes

Flow:

Figma + WDS Code Library → MCP → AI → Frontend build

Goal:

Generate working UI prototypes from design and requirements.

Key points:

- Uses WDS Code Library as dependency
- Driven by feature-level requirements (not only components)

Output:

- Functional UI (e.g. promotional banner)
- Ready for validation and iteration

---

### 2.3 Figma → CMS (Storyblok) / Micro-Frontend

Flow:

Figma + WDS Code Library → MCP → AI → Frontend → Storyblok

Goal:

End-to-end pipeline from design to CMS-ready implementation

Output:

- Frontend components (React / Next.js)
- Storyblok schemas (component models)
- Page composition
- Deployment (Vercel)

Example scope:

- 11 CMS components
- Responsive implementation
- CMS field mapping

MCP servers:

- Figma
- Storyblok
- Vercel

---

## 3. MCP (Model Context Protocol)

MCP acts as integration layer between tools and AI.

Responsibilities:

- Read Figma structure
- Access WDS components
- Generate code
- Interact with CMS
- Handle deployment

Key idea:

Single interface enabling end-to-end automation via AI

---

## 4. Key Insights

### Design → Code

- Reduces design-to-code gap
- Tokens and naming flow directly into implementation
- Eliminates interpretation differences

### Role of humans

- Shift from production → to review and QA
- Focus on decisions instead of manual implementation

### Output quality

Expected to be:

- Token-compliant
- Accessible
- Responsive
- Deployable

---

## 5. Efficiency Claims

Code Library generation:

- 2–3 days vs 6–8 weeks
- ~15–20x faster
- ~10–15x cheaper

Full workflow (incl. CMS):

- ~2.5 days vs ~5 weeks
- ~88% effort reduction

---

## 6. Critical Observations

### 6.1 WDS Code Library as central dependency

All workflows depend on WDS Code Library:

- Prototypes
- Frontend builds
- CMS integration

---

### 6.2 Figma alone is not sufficient

Explicit requirement:

Figma + product requirements (planning mode)

Implication:

Design does not contain full logic required for generation.

---

### 6.3 Iterative AI workflow

- Planning → build → iterate loop
- Changes can be applied quickly
- Supports agile experimentation

---

### 6.4 CMS as part of pipeline

- CMS schemas generated alongside frontend
- Aligns design, frontend and content structure

---

## 7. Risks (Implicit)

Not explicitly stated in the proposal, but relevant:

- Potential lack of governance
- Risk of inconsistent outputs across teams
- Possible bypass of WDS standards

---

## 8. Relation to CU Tool

Full lifecycle:

Design → Code → CMS → Production → CU Tool

CU Tool role:

- Component usage tracking
- Adoption analytics
- Feedback loop into design system

---

## 9. Interpretation

This proposal positions WDS as:

Design System → Platform

Not only:

- tokens
- components

But:

- generation system
- integration layer
- workflow engine