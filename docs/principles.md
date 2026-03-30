# WDS Principles

## Core principles

### 1. Contracts define intent

Contracts describe:
- what a component is
- what inputs it accepts
- what variants and states are allowed
- what constraints must be respected

They do NOT describe:
- how the component is rendered
- how styling is implemented

---

### 2. Implementation is replaceable

Implementation layers (e.g. React, Angular):
- consume contracts
- render UI based on them

They are:
- interchangeable
- not the source of truth

---

### 3. System over framework

The system must exist independently of:
- React
- Angular
- any specific technology

Frameworks are runtimes, not definitions.

---

### 4. Tokens define values, not behavior

Design tokens:
- provide shared values (color, spacing, typography)
- are reusable across implementations

They do NOT define:
- component logic
- allowed combinations
- behavior

---

### 5. Separation of concerns

The system is split into clear layers:

- Figma → design representation
- Model → normalized structure
- Contract → formal definition (source of truth)
- Implementation → runtime execution
- CMS / AI → consumers of the contract

---

### 6. One system, multiple implementations

A classical design system often becomes tied to a single implementation (e.g. React).

WDS enables:
- one logical system (contracts)
- multiple implementations (React, Angular, CMS rendering, AI)

---

### 7. AI consumes contracts, not design files

AI should operate on:
- structured contracts
- explicit constraints
- defined APIs

Not on:
- raw Figma files
- implicit design decisions

---

## Summary

WDS is not a UI library.

It is a **system definition layer** that:
- standardizes components
- defines rules and constraints
- enables multiple implementations to stay consistent