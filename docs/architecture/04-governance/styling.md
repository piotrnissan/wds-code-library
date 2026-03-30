# Styling Governance

Styling governance defines ownership, consistency rules, validation, and drift control for visual definitions within the WDS architecture.

It is not the place where visual definition first appears. The canonical machine-readable visual definition is established in the Visual Specification. Styling governance ensures that this definition remains correct, complete, and consistent over time.

WDS does not define styling implementations such as CSS, design tokens in runtime form, or framework-specific styling systems. Instead, WDS defines the visual rules that styling systems must interpret, and styling governance ensures those rules are maintained.

## Role of Styling Governance in WDS

Styling governance is responsible for ensuring that:
- the Visual Specification is complete and up to date
- visual rules remain consistent with the Design Layer
- no visual rule that WDS depends on exists only in Figma
- drift between design artifacts and the Visual Specification is detected and resolved
- downstream execution systems implement visual rules consistently with the specification

Styling governance does not define the visual rules themselves. That is the responsibility of the Visual Specification.

WDS defines:
- what a component is
- how it behaves
- what structure it has
- what constraints apply
- what visual rules govern its appearance (via the Visual Specification)

Styling governance ensures these visual rules are:
- owned and tracked
- validated against the Design Layer
- complete relative to what execution systems require

## Styling as Reference, Not Execution

Component Contracts may reference visual specification data, but they do not define runtime styling directly.

Examples of references include:
- semantic roles (e.g. primary, secondary, emphasis)
- token references (e.g. color.primary, spacing.medium)
- variant-level visual intent (e.g. size, tone, emphasis)

These references describe intent, not implementation.

They must not include:
- CSS rules
- framework-specific styling definitions
- hardcoded visual values tied to a specific runtime

## Styling Implementation

Styling is implemented in execution environments.

This may include:
- CSS or styling systems in frontend frameworks
- theming systems
- design tokens resolved at runtime
- platform-specific rendering rules

Different systems may implement styling differently while consuming the same Component Contract.

For example:
- a React implementation may use CSS Modules or Tailwind
- a CMS-rendered system may use predefined class mappings
- a native application may use platform-specific styling APIs

WDS does not enforce a specific styling technology.

## Relationship to Design Layer and Visual Specification

The Design Layer (e.g. Figma) is the authoring surface where visual decisions are made.

The Visual Specification extracts those decisions into machine-readable form owned by WDS.

Styling governance ensures that:
- the extraction is complete
- the Visual Specification accurately reflects the Design Layer
- changes in design are propagated to the Visual Specification
- no visual rule required by the architecture exists only in Figma

The Design Layer expresses visual intent. The Visual Specification makes it machine-readable. Styling governance makes sure nothing is lost or inconsistent between them.

## Constraints and Consistency

Although styling is external to WDS, it must remain consistent with the Component Contract.

This means:
- styling must respect structural constraints
- variants must map correctly to visual differences
- accessibility requirements must be preserved
- no visual implementation may contradict contract behaviour

If styling cannot support the contract definition, this must be treated as a capability gap, not silently adjusted.

## Architectural Boundary

Styling governance belongs to the governance layer of WDS.

It governs the Visual Specification and ensures consistency between design, specification, and execution.

Runtime styling belongs to execution systems. Styling governance does not define how styling is implemented at runtime. It ensures that execution systems have a correct and complete visual specification to work from.

This separation ensures that:
- WDS remains platform-agnostic
- multiple styling systems can coexist
- contracts and visual specifications remain stable regardless of visual implementation
- visual definition is governed, not just left to downstream interpretation