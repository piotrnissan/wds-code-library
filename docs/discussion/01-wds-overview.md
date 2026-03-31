# WDS Code Library — Overview

## Problem

Today, our design system exists across disconnected layers:
- Figma (design intent)
- ad-hoc implementations (React, CMS, etc.)
- no consistent contract between design and execution

This leads to:
- inconsistent implementations across markets
- repeated interpretation of the same components
- no reliable system-level validation
- limited ability to scale with AI or automation

---

## Core Idea

WDS Code Library introduces a structured pipeline:

Planning → Design → Visual Specification → System Model → Component Contract → Adapters

Where:

- Planning defines intent and rules
- Design defines visual structure (Figma)
- Visual Specification translates design into machine-readable form
- System Model acts as a transformation and normalization layer:
  - validates inputs from design and visual specification
  - resolves inconsistencies and ambiguity
  - produces a clean, structured representation ready for contract generation
- Component Contract becomes the single source of truth
- Adapters translate contracts into execution (React, CMS, AI)

---

## Key Principle

Component Contract is the central artifact.

Everything else either:
- feeds into it (Planning, Design, Visual Spec)
- or consumes it (Adapters, AI, platforms)

---

## What This Enables

- Consistent implementation across markets
- Clear separation between design and execution
- Deterministic system behavior (not interpretation-based)
- AI systems consuming structured data instead of prompts
- Scalability beyond a single framework (React is just a reference)
- Human-controlled system evolution (AI-assisted, but not AI-driven)

---

## What This Is NOT

- Not a UI library (no CSS or styling implementation)
- Not tied to a single framework or CMS
- Not replacing Figma — Figma remains the design source

---

## Current State

- Architecture defined and structured
- End-to-end example (Button) created
- Core artifacts identified (Visual Spec, System Model, Contracts)
- Open questions and decisions clearly mapped

---

## Goal of This Discussion

Align on:
- direction (is this the right system model?)
- ownership boundaries
- key architectural decisions before implementation