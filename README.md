# Takeat UI Kit

Official Design System and interface guidelines for Takeat products.

This repository is the **single source of truth for Takeat interface design**.

It defines the visual foundations, design tokens, components, states, usage guidelines, and platform-specific rules that should be followed when designing, prototyping, or developing Takeat interfaces.

---

## Design System Documentation

The complete Takeat Design System is defined in two documents.

### Foundations

`foundations.md` defines the fundamental visual language of Takeat, including:

* Colors
* Semantic color tokens
* Light and Dark modes
* Typography
* Font weights
* Spacing
* Grids
* Border radius
* Shadows
* Platform-specific foundations

Read the complete document:

**https://raw.githubusercontent.com/takeat-design/UIKIT/main/foundations.md**

---

### Components

`components.md` defines the components used across Takeat interfaces, including:

* Component anatomy
* Sizes
* Variants
* Properties
* States
* Interaction behavior
* Platform-specific behavior
* Usage guidelines
* Do's and Don'ts

Read the complete document:

**https://raw.githubusercontent.com/takeat-design/UIKIT/main/components.md**

---

# Instructions for AI

This repository may be provided as a design context to an AI tool.

If you are an AI system generating, designing, prototyping, reviewing, or modifying a Takeat interface, follow the rules below.

## 1. Takeat Design System is the source of truth

For **UI and visual design decisions**, `foundations.md` and `components.md` are the **exclusive source of truth**.

You must use these documents as the authoritative reference for Takeat interface design.

Do not replace, reinterpret, or override the Takeat Design System with another design approach.

---

## 2. Read both documents

The README is only the entry point.

Before making significant UI or visual design decisions, read and apply the relevant information from both:

1. `foundations.md`
2. `components.md`

Direct sources:

* `https://raw.githubusercontent.com/takeat-design/UIKIT/main/foundations.md`
* `https://raw.githubusercontent.com/takeat-design/UIKIT/main/components.md`

Do not assume that the README contains the complete Design System.

---

## 3. Do not use external Design Systems

For Takeat UI design, **do not use another Design System as a substitute**.

This includes, but is not limited to:

* Material Design
* Material UI
* Apple Human Interface Guidelines
* iOS Design Guidelines
* macOS Design Guidelines
* Bootstrap
* Ant Design
* Chakra UI
* Tailwind UI
* shadcn/ui
* Fluent UI
* Carbon Design System
* Atlassian Design System
* Any other third-party Design System

If a third-party Design System conflicts with Takeat's Design System, **the Takeat Design System always takes precedence**.

---

## 4. Use existing Takeat tokens

When an official token exists, use it.

Do not invent or approximate:

* Colors
* Font families
* Font sizes
* Font weights
* Line heights
* Letter spacing
* Spacing values
* Grid values
* Border radii
* Shadows
* Component dimensions

If a suitable token exists in `foundations.md`, use the official token.

Do not replace an official token with a visually similar custom value.

---

## 5. Use existing Takeat components

Before creating a new component or interaction pattern, check `components.md`.

If an appropriate Takeat component exists, use it.

Follow its documented:

* Anatomy
* Size
* Variant
* Properties
* States
* Typography
* Colors
* Spacing
* Interaction behavior
* Platform-specific rules

Do not create a new component when an existing Takeat component can satisfy the requirement.

---

## 6. Follow platform-specific rules

Takeat interfaces may have different specifications depending on the target platform.

Always identify the applicable platform:

* Desktop
* Mobile / Tablet
* Totem

Do not automatically transfer dimensions, typography, spacing, interaction patterns, or touch targets from one platform to another.

Follow the platform-specific rules defined in `foundations.md` and `components.md`.

---

## 7. Follow Light and Dark mode rules

Takeat supports Light and Dark modes.

Use the official semantic color tokens defined in `foundations.md`.

Do not create independent colors for Dark mode when an official semantic token already exists.

Do not replace semantic tokens with arbitrary hex values when an appropriate semantic token is available.

---

## 8. Follow existing usage rules

The Design System contains not only visual specifications but also rules about **when and how components should be used**.

Examples include:

* Component variants
* Button hierarchy
* Component states
* Platform restrictions
* Touch targets
* Spacing relationships
* Color semantics
* Typography hierarchy
* Do's and Don'ts

These rules are mandatory when they apply to the interface being created.

---

# Handling Missing Design Rules

The Takeat Design System may not yet define every possible interface pattern.

If a requirement is not explicitly covered:

### First

Check whether an existing Takeat token, component, or pattern can solve the requirement.

### Second

Use the closest existing Takeat pattern and remain consistent with the established Design System.

### Third

If a genuinely new pattern is required, create the **simplest possible solution consistent with the existing Takeat Design System**.

Do not introduce an external Design System or external visual pattern to fill the gap.

A new pattern must be treated as a **proposed extension of the Takeat Design System**, not as an existing official component.

Do not claim that a newly created pattern is an official Takeat component unless it is documented in `components.md`.

---

# Design Decision Priority

For UI and visual design decisions, follow this order of authority:

### 1. `foundations.md`

Visual foundations and design tokens.

### 2. `components.md`

Component specifications and usage rules.

### 3. Product requirements

What the interface needs to accomplish.

Product requirements determine the functionality and content of a screen, but should be implemented using the Takeat Design System whenever possible.

### No external Design System

There is **no third-party Design System, UI library, external visual reference, or generic design convention that should override or supplement the Takeat Design System for Takeat UI decisions**.

---

# Important AI Constraint

When designing a Takeat interface, do not think:

> "What would be the best design according to general UI/UX practices?"

Instead, think:

> "How should this requirement be solved using the existing Takeat Design System?"

The goal is not to create a generic modern interface.

The goal is to create a **Takeat interface that is consistent with the existing Takeat Design System**.

---

# Repository Structure

```text
UIKIT/
├── README.md
├── foundations.md
└── components.md
```

### `README.md`

Entry point for humans and AI tools.

Provides the Design System scope, AI instructions, and links to the complete documentation.

### `foundations.md`

Defines the visual foundations and tokens of the Takeat Design System.

### `components.md`

Defines the components, variants, states, behavior, and usage guidelines of the Takeat Design System.

---

# Official Sources

## Design Context Entry Point

Use this URL when providing the Takeat Design System as a single context source to an AI tool:

**https://raw.githubusercontent.com/takeat-design/UIKIT/main/README.md**

## Foundations

**https://raw.githubusercontent.com/takeat-design/UIKIT/main/foundations.md**

## Components

**https://raw.githubusercontent.com/takeat-design/UIKIT/main/components.md**

---

# Using This Repository With AI Tools

To provide the Takeat Design System as context to an AI tool, use the following URL:

**https://raw.githubusercontent.com/takeat-design/UIKIT/main/README.md**

The AI tool should then read the two official Design System documents referenced by this README:

* `foundations.md`
* `components.md`

If the AI tool cannot access external URLs, provide `foundations.md` and `components.md` directly as context.

The content of this repository should be treated as the authoritative Design System context for Takeat UI.

---

# Keeping the Design System Consistent

When the Takeat Design System evolves, update the appropriate source document:

* Update `foundations.md` when changing foundations or tokens.
* Update `components.md` when changing components or component behavior.
* Update `README.md` only when changing the repository structure, AI instructions, documentation scope, or source locations.

Avoid duplicating Design System specifications across files.

`foundations.md` and `components.md` are the actual Design System documentation.

`README.md` is the entry point and instruction layer.
