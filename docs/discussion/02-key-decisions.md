# Key Architectural Decisions

This document highlights the most important decisions already made in the architecture.

---

## 1. Component Contract as Single Source of Truth

Component Contracts are the central artifact of the system.

- All execution systems consume contracts
- All upstream layers feed into contracts

This removes ambiguity between design and implementation.

---

## 2. Separation of Visual Specification from Contracts

Visual Specification is intentionally separated from Component Contracts.

- Visual Spec = how it looks
- Contract = what it is and how it behaves

This allows:
- market-level visual customization
- stable functional definitions

---

## 3. Canonical Flow Definition

The system follows a strict transformation pipeline:

Planning → Design → Visual Spec → System Model → Contract → Adapters

Each step has a clearly defined responsibility.

---

## 4. No Styling Implementation in WDS

WDS does NOT define CSS or styling implementation.

Instead:
- it defines tokens and mappings
- execution systems implement styling

This avoids coupling WDS to specific frameworks.

---

## 5. System Model as Normalization Layer

System Model is responsible for:
- validating inputs
- normalizing data
- resolving inconsistencies into a deterministic definition
- preparing contracts

It is NOT an execution layer, and remains fully deterministic (AI may assist upstream, but not define the system).

---

## 6. AI as a First-Class Consumer

AI is treated as a system consumer of contracts.

This implies:
- structured inputs over prompt-only systems
- deterministic outputs where possible

---

## 7. Contracts Are Framework-Agnostic

WDS is not React-specific.

- React is a reference implementation
- Contracts must be consumable by multiple systems (CMS, AI, etc.)

---

## Why This Matters

These decisions define:
- system boundaries
- ownership model
- scalability potential

They should be validated before moving into implementation.