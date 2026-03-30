# WDS Code Library

WDS Code Library is the strategic source of truth for the WDS system model.

This repository is intended to define and document:
- component contracts
- the relationship between Figma, model, AI, development, and CMS
- ownership and workflow principles
- future framework-agnostic tooling directions

## What this repository is
- a documentation and system-model repository
- a place to define component contracts and related concepts
- a foundation for future tooling and generators

## How WDS fits into the system

WDS Code Library sits between design and implementation.

It defines a contract layer that connects:

Figma (design) → WDS (contracts) → AI / generators → frontend implementations → CMS

Key idea:

- Figma defines visual intent
- WDS defines system structure and rules
- AI and adapters generate implementations based on WDS contracts

This allows:
- consistent generation across teams
- framework-agnostic implementations
- alignment between design, code, and CMS

## What this repository is not
- not a React component library
- not an implementation repository
- not tied to any single framework
- not a production CMS integration

## Current focus
At this stage, the focus is on:
- structure
- documentation
- shared terminology
- component workflow
- early contract examples

## Repository structure
- `docs/` — documentation and working design/system documents
- `model/` — future home of internal model and contract artifacts
- `tooling/` — placeholder for future generators, validators, or automation

## Initial document set
- WDS Component Workflow
- Component Contracts
- Figma → Model → Contract Mapping
- Ownership Model