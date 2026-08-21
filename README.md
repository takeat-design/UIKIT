# Takeat UI Kit

Design system and interface guidelines for building Takeat product interfaces.

This repository is the **source of truth for Takeat UI design**. When creating, modifying, or prototyping an interface, always follow the rules, tokens, components, and usage guidelines defined here.

## Documentation

### `foundations.md`

Defines the visual foundations of the Takeat Design System:

* Colors and semantic tokens
* Light and Dark modes
* Typography
* Spacing
* Grids
* Border radius
* Shadows
* Platform-specific foundations

Use this file to understand **how Takeat interfaces should look and behave at a foundational level**.

### `components.md`

Defines the components used across Takeat interfaces:

* Component anatomy
* Sizes
* Variants
* States
* Properties
* Usage guidelines
* Do's and Don'ts
* Platform-specific behavior

Use this file to understand **which components to use and how to use them correctly**.

## Rules for AI

When generating or modifying Takeat interfaces:

1. **Follow this Design System as the source of truth.**
2. **Use existing tokens and components whenever applicable.**
3. **Do not invent new colors, typography styles, spacing values, radii, shadows, or component variants when an existing option is available.**
4. **Follow the semantic color tokens and platform-specific rules defined in `foundations.md`.**
5. **Follow component usage, sizing, states, and interaction rules defined in `components.md`.**
6. **Do not create visually inconsistent alternatives when an existing Design System pattern can solve the requirement.**
7. **Respect Desktop, Mobile, and Totem-specific rules.**
8. When a requirement is ambiguous, prefer the existing Design System pattern over creating a new solution.
9. If a new pattern is genuinely required and no existing component or rule applies, keep the solution consistent with the foundations and clearly identify it as a new pattern.

## Priority

When designing an interface, use the following order of authority:

**1. `foundations.md` → visual foundations and tokens**

**2. `components.md` → component specifications and usage**

Do not override these rules based solely on visual preference.

## Repository Structure

```text
UIKIT/
├── README.md
├── foundations.md
└── components.md
```

The documentation is intentionally separated into **foundations** and **components** so that both visual rules and component behavior can be consistently applied across Takeat products.
