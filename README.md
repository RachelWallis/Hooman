# Hooman Design Tokens

Three-layer design token set, authored in Token Studio and version-controlled as a single tokens.json.

Hooman is an experiment in setting up design tokens to link with a real design system in Figma. The premise being that a single source of truth is the one that stops ambiguity and diverging design decisions between Designers and Developers.

## The layering

Three layers, each referencing only the one beneath it.

**Primitives** — `base-colour`, `base-dimension`, `base-font`. Raw values with no meaning attached. `base-dimension.100` is `1rem`; the rest of the scale is composed from it.

**Semantic** — `surface.page`, `surface.info`. Primitives given a job.

**Component** — `button`, `card`, `header`, `footer`, `navigation`, `icons`,`tags`. What a specific thing uses.

## Composition and aliasing

Values are referenced, never repeated. `button.primary.bg` resolves to `{base-colour.secondary.green}` rather than restating a hex. Dimensions compose arithmetically — `{base-dimension.100} * 2.0` — so the scale has one source and moving the base moves everything derived from it.

## Format

Token Studio JSON: `value` / `type` pairs with `$extensions` for modifiers.
Used in Figma to poulate the design system build.

## Future Plans

The semantic layer is thin relative to the component layer — two named surfaces against seven component groups — so components reach past semantics to primitives more often than they should. The fix is to widen the semantic layerfirst, so components have something meaningful to bind to.
