# Governance and Versioning

Governance and versioning define how Component Contracts evolve over time while preserving system integrity, predictability, and compatibility across all downstream consumers.

WDS is a contract-first system. Any change to a Component Contract has direct impact on all systems that consume it. Governance ensures that these changes are controlled, explicit, and traceable.

## Contract Versioning

Each Component Contract must have an explicit version.

Versioning exists to:
- track changes to component definitions
- communicate impact to downstream systems
- enable safe evolution without breaking consumers
- support parallel versions when necessary

Versioning should follow semantic principles:

- **Major version**  
  Introduced when breaking changes are made to the contract  
  (e.g. removing fields, changing required properties, altering structure or constraints)

- **Minor version**  
  Introduced when backward-compatible capabilities are added  
  (e.g. new optional fields, additional variants, extended constraints)

- **Patch version**  
  Introduced for non-functional or non-breaking adjustments  
  (e.g. clarifications, metadata updates, documentation-level changes)

A Component Contract version is part of its identity and must be included in all downstream usage.

## Change Management

All changes to Component Contracts must be intentional, reviewed, and traceable.

Change Management ensures that:
- changes are evaluated before being applied
- impact is understood across all consumers
- decisions are documented
- evolution is controlled, not incidental

A typical change flow includes:
1. proposal of change (design, behaviour, structure, or constraints)
2. impact analysis across existing consumers
3. classification of change (major, minor, patch)
4. approval (human-in-the-loop)
5. version update
6. contract update
7. communication to downstream systems

Changes must never be applied silently or implicitly.

## Backward Compatibility

Backward compatibility determines whether existing consumers can continue to operate without modification after a contract change.

Changes can be classified as:

- **Backward-compatible**
  - adding optional fields
  - extending allowed values
  - introducing new variants without affecting existing ones

- **Breaking**
  - removing fields
  - changing required fields
  - altering structure or composition rules
  - tightening constraints in a way that invalidates existing usage

Breaking changes require a major version increment and must not be applied in place.

Backward compatibility is a design decision, not a side effect. It must be explicitly evaluated for every change.

## Consumer Impact

Every change to a Component Contract affects downstream consumers.

Consumers may include:
- frontend implementations
- CMS schemas
- AI systems and pipelines
- validation and testing systems

Governance must ensure that:
- consumers are aware of version changes
- impact is clearly communicated
- migration paths are defined when needed
- multiple versions can coexist where required

Consumers must not assume that contracts remain static.

## Version Coexistence

In some cases, multiple versions of a Component Contract may need to coexist.

This may occur when:
- consumers cannot upgrade immediately
- migrations require phased rollout
- legacy systems must be supported temporarily

In such cases:
- each version must remain fully defined and valid
- adapters must explicitly support specific versions
- no implicit merging of versions is allowed

Version coexistence must be treated as a temporary state, not a permanent solution.

## Governance Boundaries

Governance applies to the WDS core and its outputs.

Execution systems:
- must respect contract versions
- must not override contract rules
- may enforce additional runtime constraints, but cannot redefine canonical behaviour

WDS defines what a component is.  
Governance defines how that definition evolves.