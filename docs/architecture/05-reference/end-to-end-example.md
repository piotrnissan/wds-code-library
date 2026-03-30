# End-to-End Example

This example traces a single component — Button — through the full WDS architecture, from planning intent to downstream execution.

WDS is a contract-first control layer between design and execution. It defines both semantic and visual definition for each component, then produces machine-readable outputs that downstream systems consume. WDS is not a UI library, not a CMS, and not an AI pipeline. It is the canonical authority.

The architecture flow:

Planning → Design Layer → Visual Specification → System Model → Component Contract → Execution

## Component: Button

## 1. Planning Layer

The Planning Layer defines the component in terms of intent, behavioural rules, and constraints. No visual design or implementation exists at this stage.

Intent:
- trigger an action
- communicate importance through three distinct emphasis levels
- adapt to light and dark background contexts

Behavioural rules:
- must have content (label or equivalent)
- supports three emphasis levels: primary (highest), secondary (medium), tertiary (lowest)
- must support a disabled state that prevents interaction
- must support light and dark themes
- must support a full-width layout mode
- must support a restricted mobile size variant

Constraints:
- content is the only required property; all others have defaults
- size "mobile" is restricted use — requires WDS governance approval
- disabled state must fully suppress interaction
- tertiary is structurally distinct from primary and secondary (column layout with underline affordance)

## 2. Design Layer

The Design Layer is where visual intent is authored. For WDS, the authoring environment is Figma.

In Figma, designers define:
- visual forms for each variant: primary as filled pill, secondary as outlined pill, tertiary as text with underline bar
- colour assignments per variant and theme (light/dark)
- typography roles mapped to WDS token families
- interaction states: hover, focus, disabled
- spacing, padding, and shape

Figma is not the final system artefact. It is the source of visual intent. WDS extracts this intent into a machine-readable Visual Specification that becomes part of the canonical definition.

## 3. Visual Specification

The Visual Specification is the machine-readable representation of all visual rules for the component. WDS owns this artefact. It is derived from the Design Layer and exists independently of any execution runtime.

All visual properties are defined as functions of visual axes (variant, size, state, theme). Each combination resolves to a complete and explicit visual definition.

### Visual Axes

The Button's visual appearance resolves across four axes:
- variant: primary, secondary, tertiary
- theme: light, dark
- state: default, hover, focus, disabled
- size: default, mobile

### Typography

Default size uses the action-button token family:
- font-family: --wds-font-family-nissan
- font-size: --wds-type-action-button-size
- line-height: --wds-type-action-button-line
- letter-spacing: --wds-type-action-button-spacing
- font-weight: --wds-font-weight-bold
- text-transform: uppercase

Mobile size (restricted use) overrides to the action-filter token family:
- font-size: --wds-type-action-filter-size
- line-height: --wds-type-action-filter-line
- letter-spacing: --wds-type-action-filter-spacing
- font-weight, font-family, and text-transform remain unchanged

### Colour Mapping

Primary — light:
- default: background --wds-color-nissan-black, text --wds-color-nissan-white
- hover: background --wds-color-action-hover-onlight
- disabled: background --wds-color-action-disabled-onlight, text --wds-color-nissan-grey

Primary — dark:
- default: background --wds-color-nissan-white, text --wds-color-nissan-black
- hover: background --wds-color-action-hover-ondark
- disabled: background --wds-color-action-disabled-ondark, text --wds-color-action-disabled-onlight

Secondary — light:
- default: background transparent, text --wds-color-nissan-black, border --wds-color-nissan-black
- hover: border thickens from 2px to 4px, colour unchanged
- disabled: text --wds-color-action-disabled-onlight, border --wds-color-action-disabled-onlight

Secondary — dark:
- default: background transparent, text --wds-color-nissan-white, border --wds-color-nissan-white
- hover: border thickens from 2px to 4px, colour unchanged
- disabled: text --wds-color-action-disabled-ondark, border --wds-color-action-disabled-ondark

Tertiary — light:
- default: text --wds-color-nissan-black, underline bar --wds-color-nissan-black
- hover: text --wds-color-action-hover-onlight, underline bar hidden
- disabled: text --wds-color-action-disabled-onlight, underline bar --wds-color-action-disabled-onlight

Tertiary — dark:
- default: text --wds-color-nissan-white, underline bar --wds-color-nissan-white
- hover: text --wds-color-action-hover-ondark, underline bar hidden
- disabled: text --wds-color-action-disabled-ondark, underline bar --wds-color-action-disabled-ondark

### Shape and Border

Primary and secondary (pill form):
- border-radius: 40px
- padding: 12px 30px (default), 6px 20px 8px (mobile)
- primary has no border
- secondary has a 2px inset border (must not cause layout shift)

Tertiary:
- no border-radius (except 2px on focus ring)
- transparent background
- padding: 11px top / 3px bottom (default), 5px top / 3px bottom (mobile)
- underline bar: 2px height, full content width, 8px gap below label (default) or 4px gap (mobile)

### Focus

All variants use a 4px outer ring as the focus indicator. Focus is visible only on keyboard navigation, not pointer interaction.

- light theme: --wds-color-action-focus-onlight
- dark theme: --wds-color-action-focus-ondark
- secondary: ring is layered outside the existing inset border
- tertiary: ring shape uses 2px border-radius
- native outline is suppressed in favour of the ring

### Interaction Behaviour

Hover (suppressed when disabled):
- primary: background shifts to action-hover token
- secondary: border thickens from 2px to 4px, no fill change
- tertiary: text shifts to action-hover token, underline bar hides (layout-preserving — opacity, not removal)

Disabled:
- cursor indicates non-interactive state
- all hover and focus behaviour is suppressed
- colours shift to action-disabled tokens per theme

### Motion

- primary and secondary: all visual properties transition at 200ms
- tertiary: colour transitions at 200ms; underline bar opacity transitions at 200ms independently
- no easing function is specified (platform default)

## 4. System Model

The System Model is the internal convergence layer. It reconciles the semantic definition from the Planning Layer with the visual definition from the Visual Specification into a single canonical model.

This model is not exposed externally. It exists to ensure that semantic rules and visual rules are consistent before the Component Contract is generated.

If inconsistencies exist between semantic and visual definitions, the System Model must either resolve them deterministically or surface them as structural errors.

For Button, the reconciled model contains:

- type: Button
- variants: [primary, secondary, tertiary]
- states: [default, disabled]
- themes: [light, dark]
- sizes: [default, mobile]
- properties:
  - variant (optional, defaults to "primary")
  - children (required, node)
  - fullWidth (optional, boolean, defaults to false)
  - theme (optional, defaults to "light")
  - size (optional, defaults to "default", restricted use)
  - className (optional, string, defaults to "")
  - disabled (optional, boolean, defaults to false)
- structural rules:
  - tertiary renders as column layout with child underline element
  - primary and secondary render as inline pill form
- visual rules: resolved from Visual Specification (token mappings, colour matrix, shape, interaction, motion)
- constraints:
  - children is required
  - size "mobile" requires governance approval
  - disabled suppresses all interaction

## 5. Component Contract

The Component Contract is the canonical external output of WDS. It defines semantics, structure, constraints, and allowed values. It references the Visual Specification for visual rules rather than inlining all visual detail.

Downstream systems consume the contract (and the visual definition it references) to build their implementations.

```json
{
  "component": "Button",
  "variants": ["primary", "secondary", "tertiary"],
  "states": ["default", "disabled"],
  "themes": ["light", "dark"],
  "sizes": ["default", "mobile"],
  "props": {
    "variant": { "type": "'primary' | 'secondary' | 'tertiary'", "required": false, "default": "primary" },
    "children": { "type": "node", "required": true },
    "fullWidth": { "type": "boolean", "required": false, "default": false },
    "theme": { "type": "'light' | 'dark'", "required": false, "default": "light" },
    "size": { "type": "'default' | 'mobile'", "required": false, "default": "default" },
    "className": { "type": "string", "required": false, "default": "" },
    "disabled": { "type": "boolean", "required": false, "default": false }
  },
  "constraints": [
    "children is required",
    "size 'mobile' is restricted use — requires WDS governance approval",
    "disabled prevents interaction"
  ],
  "accessibility": {
    "role": "button",
    "keyboard": "Enter and Space",
    "focus": "visible focus indicator on keyboard navigation"
  },
  "visualSpec": "ref:button/visual-specification"
}
```

The contract plus its referenced Visual Specification together form the complete canonical definition.

## 6. Execution: UI Adapter

A UI Adapter translates the contract and its Visual Specification into a frontend implementation. It consumes both WDS outputs — it does not interpret Figma directly.

The current React/CSS realization:

- generates a ButtonProps interface extending React.ButtonHTMLAttributes<HTMLButtonElement>
- children is typed as React.ReactNode
- maps each variant × theme combination to a CSS Module class (primaryLight, primaryDark, secondaryLight, secondaryDark, tertiaryLight, tertiaryDark)
- maps size to modifier classes (pillMobile, tertiaryMobile)
- maps fullWidth to a fullWidth class
- tertiary renders a distinct DOM structure (column flex container with child underline span)
- realizes all visual tokens via CSS custom properties (var(--wds-*))
- realizes hover via :hover:not(:disabled), focus via :focus-visible, disabled via :disabled
- uses inset box-shadow for secondary borders; compound box-shadow for focus + border layering
- uses opacity for tertiary underline hiding (layout-preserving)
- uses class composition via filter(Boolean).join(' ')
- spreads remaining HTML attributes via ...props

The adapter does not redefine behaviour or visual rules. It realizes what WDS defines.

## 7. Execution: CMS Adapter

A CMS Adapter translates the contract into editorial structures. It consumes the contract to generate constrained content fields.

- creates fields for: children (label content), variant (select: primary / secondary / tertiary), theme (select: light / dark), size (select: default / mobile), fullWidth (boolean), disabled (boolean)
- restricts variant to the three allowed values
- restricts size to the two allowed values, with "mobile" flagged as restricted use
- enforces children as a required field

Editors interact with the component through these constrained structures. Visual rendering is handled by the UI adapter at display time.

## 8. Execution: AI Adapter

An AI Adapter translates the contract into structured rules for AI systems.

- allowed values:
  - variant: primary | secondary | tertiary
  - theme: light | dark
  - size: default | mobile
- required fields:
  - children (must always be provided)
- optional fields with defaults:
  - variant → "primary"
  - theme → "light"
  - size → "default"
  - fullWidth → false
  - disabled → false
  - className → ""
- restrictions:
  - size "mobile" is restricted — must not be used unless explicitly allowed by higher-level instruction or governance context
  - values outside allowed sets must be rejected
  - omitted optional fields must use their defined defaults

The AI system does not invent component rules. It operates within the contract.

## 9. Change Example (Versioning)

A change is introduced:

- new size: "compact"

Impact:

- added to sizes in the contract
- added to the Visual Specification (new typography and spacing mappings)
- does not affect existing sizes or variants

This is a minor version change:

```
1.0.0 → 1.1.0
```

Downstream systems:

- UI adapter adds new size modifier class and token mappings
- CMS adapter exposes new size option
- AI adapter includes new size in allowed outputs

No existing usage breaks.

## 10. Breaking Change Example

Change:

- variant "tertiary" is removed

Impact:

- existing implementations using variant="tertiary" become invalid
- tertiary entries removed from contract, Visual Specification, and all adapters

This is a major version change:

```
1.1.0 → 2.0.0
```

Required actions:

- consumers must update usage to primary or secondary
- adapters must remove tertiary mappings
- pipelines must validate compatibility

## Summary

This example demonstrates the WDS architecture:

- WDS defines both semantic definition (intent, rules, constraints) and visual definition (tokens, colours, shape, interaction, motion)
- Visual Specification is a first-class WDS artefact, owned by WDS, not left implicit in Figma
- the System Model reconciles semantic and visual inputs into a single canonical model
- the Component Contract is the external output, referencing the Visual Specification for visual rules
- execution systems (UI, CMS, AI) realize WDS definitions — they do not invent them
- one canonical architecture supports multiple downstream systems without coupling them together
- changes are controlled through versioning and governance
- WDS acts as a design compiler: transforming authored intent into canonical system definitions that can be consistently realized across multiple platforms.
