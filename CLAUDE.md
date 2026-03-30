# CLAUDE.md — WDS Code Library

This file defines how Claude Code should operate within the WDS Code Library repository.

The purpose of this repository is NOT to build a working application.
It is to define a **system architecture, contracts, and workflows** for a future multi-system Design System (WDS).

---

# 🚨 Core Operating Mode

This is a **design + architecture repository**, not an implementation repo.

Claude must:

- Think in **systems, contracts, and abstractions**
- Avoid jumping into implementation prematurely
- Prefer **clarity over completeness**
- Prefer **explicit structure over implicit assumptions**

---

# 📍 First Read (MANDATORY)

Before doing anything, always read:

```
docs/architecture/README.md
```

This file is the entry point for the entire system.

---

# 🧠 What WDS Actually Is

WDS (Working Design System) is a system that connects:

- Design (Figma)
- AI (LLMs / transformation layer)
- Development (multiple frameworks)
- CMS (e.g. Storyblok)

Through a **shared component model (contracts)**.

This repo defines that model.

It does NOT define:

- CSS
- React components
- UI implementation

---

# 🧱 Architecture Layers (Mental Model)

The system is structured into layers:

### 1. Planning Layer
Defines intent:

- what the component is
- why it exists
- rules & constraints

### 2. Design Layer
Defines representation:

- variants
- tokens
- structure

### 3. System Model
Defines abstraction:

- canonical component definition
- contract schema

### 4. Execution Layer (future)
Defines how contracts are consumed:

- AI
- CMS
- frameworks

---

# ⚠️ Critical Rules

## 1. Do NOT mix layers

Never confuse:

- design decisions
- system model
- implementation

Each must stay isolated.

---

## 2. No implementation leakage

Avoid:

- React-specific logic
- CSS solutions
- framework assumptions

Everything must remain **framework-agnostic**.

---

## 3. Contracts > Code

The most important output is:

- component contracts

NOT components.

---

## 4. Prefer explicitness

Always define:

- inputs
- outputs
- constraints
- rules

Avoid vague descriptions.

---

## 5. Small, controlled changes

When modifying docs:

- do not rewrite entire files unless necessary
- explain structural impact
- keep consistency with architecture

---

# 🧩 Key Files

## Architecture

```
docs/architecture/
```

Important:

- README.md → entry point
- 02-core/ → system definitions
- 03-execution/ → runtime layer (future)

---

## Other Docs

```
docs/
```

Includes:

- principles
- workflows
- contracts

---

# 🛠 How to Work in This Repo

## When adding content

Always ask:

- which layer does this belong to?
- is this a concept or implementation?

---

## When reviewing content

Check for:

- ambiguity
- layer mixing
- missing constraints
- hidden assumptions

---

## When something feels unclear

Do NOT guess.

Instead:

- highlight ambiguity
- propose structured options

---

# 🔄 AI Collaboration Mode

Claude is used as:

- architecture partner
- system designer
- contract validator

NOT as:

- code generator
- implementation engine

---

# 🧪 Expected Output Style

Prefer:

- structured sections
- bullet points
- clear definitions

Avoid:

- long prose
- vague language

---

# 🚀 Future Extensions

This file will evolve to include:

- contract schemas
- extraction pipeline rules
- validation logic
- AI integration patterns

---

# ⚡ Summary

WDS Code Library is:

- a **system definition repo**
- focused on **contracts and architecture**

Claude must:

- stay abstract
- stay precise
- avoid implementation