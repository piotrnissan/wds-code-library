# WDS Code Library

WDS Code Library is the strategic source of truth for the WDS system model.

It defines how design, AI, and engineering connect through a shared contract layer.

---

## Why this exists

Modern design systems break at scale because:
- design lives in Figma
- code lives in multiple frameworks
- CMS structures diverge per market
- AI generation lacks a reliable source of truth

WDS introduces a **contract layer** that sits between design and implementation.

This enables a single system definition to drive:
- AI generation
- frontend implementations
- CMS structures
- cross-team consistency

---

## System overview

WDS Code Library sits between design and implementation:

Figma (design) → WDS (contracts) → AI / generators → frontend → CMS

Key roles:

- **Figma** → defines visual intent  
- **WDS** → defines structure, rules, and constraints  
- **AI / tooling** → generates implementations  
- **Frontend / CMS** → consume the output  

---

## What this repository is

- a **system-model and documentation repository**
- the **source of truth for component contracts**
- a foundation for **AI-driven generation and tooling**
- a place to define **rules, constraints, and workflows**

---

## What this repository is not

- not a React component library  
- not an implementation repository  
- not tied to any single framework  
- not a production CMS integration  

---

## Current focus

This project is in an early, architecture-first stage.

Current priorities:
- defining system structure  
- establishing shared terminology  
- designing component workflows  
- exploring contract-driven generation  

---

## Repository structure

- `docs/` — architecture, workflows, and system documentation  
- `model/` — internal model and contract artifacts (future)  
- `tooling/` — generators, validators, and automation (future)  

---

## Key documents

- WDS Component Workflow  
- Component Contracts  
- Figma → Model → Contract Mapping  
- Ownership Model  

---

## Status

Exploratory / early-stage.

This repository defines direction and architecture, not production-ready implementation.