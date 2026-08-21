# Takeat UI Kit — Components

Component specifications for Takeat product interfaces. All components use Poppins and reference foundation tokens defined in `foundations.md`. Color references use the `Colors` variable collection (Light/Dark modes) — prefer semantic tokens (`text/*`, `surface/*`, `stroke/*`) and color family tokens (`red/*`, `teal/*`, `gestor/*`, etc.) over raw hex values.

---

## 1. Buttons

**Anatomy:** Icon (optional, scales with the button) | Label (typography token for the size) | Container (clickable surface with padding, radius, fill).

### Sizes
Never mix sizes across platforms.

| Size | Height | Pad V | Pad H | Radius | Typography | Icon | Icon-only | Platform |
|------|--------|-------|-------|--------|-----------|------|-----------|----------|
| Small | 24px | 4px | 8px | 4px | 12/600 (Body Small/SemiBold) | 16px | 24x24 | Desktop |
| Medium | 32px | 10px | 16px | 8px | 14/600 (Label Large/SemiBold) | 20px | 32x32 | Desktop |
| Large | 40px | 8px | 16px (24px label-only) | 12px | 14/600 (Label Large/SemiBold) | 24px | 40x40 | Desktop |
| Mobile/Tablet | 48px | 12px | 16px (24px label-only) | 12px | 16/600 (Title Small/SemiBold) | 24px | 48x48 | Mobile |
| Totem | 68px | 16px | 16px (24px label-only) | 16px | 24/600 (Heading Small/SemiBold) | 36px | 68x68 | Totem |

- Small: dense secondary actions (row actions, inline filters).
- Medium: desktop secondary button — modal footers, sidebar, list items.
- Large: primary desktop default.
- Mobile: all actions (min 48px touch target).
- Totem: all actions (min 68px for touch at kiosk distance).

### Styles
At most two styles per screen.

- **Filled** — strongest weight. Primary action (max 2 per screen). Background = brand color, text = `text/inverted`.
- **Outlined** — medium weight. Secondary actions. Transparent background, 1px brand border, brand text.
- **Tonal** — medium-low weight. Supporting actions. Brand tint background (`red/tint` at rest), brand text, no border.
- **Text Button** — lowest weight. Tertiary/destructive, links, inline actions. Transparent background (hover = `neutral/50`). Text 1: standard label; Text 2: secondary label (neutral/destructive).

### States
States change only fill/border — typography and layout stay identical. Example with Red brand:

| State | Filled bg | Outlined bg | Tonal bg | Text bg |
|-------|-----------|-------------|----------|---------|
| Rest | `red/default` | Transparent | `red/tint` | Transparent |
| Hover | `red/dark` | `red/tint` | `red/60` | `neutral/50` |
| Pressed | `red/80` | `red/60` | `red/80` | `neutral/100` |
| Focus | `red/default` + ring | Transparent + ring | `red/tint` + ring | Transparent + ring |
| Disabled | `surface/fill` | `surface/fill` | `surface/fill` | Transparent |
| Loading | `red/default` + spinner | Transparent + spinner | `red/tint` + spinner | Transparent + spinner |

**Disabled text:** `text/disabled` (all styles).

> **Gestor / Multilojas:** swap all `red/*` tokens for the `gestor/*` equivalents — `gestor/default`, `gestor/dark`, `gestor/tint`, `gestor/40`, `gestor/60`, `gestor/80`. Label on Filled stays `text/inverted`.

### Icons in buttons
The icon scales with the size (never a fixed 24px): Small 16 | Medium 20 | Large 24 | Mobile 24 | Totem 36.
- Icon-only is always square (height = width).
- The icon inherits the label color for its current state.
- Icon-only requires an `aria-label` or tooltip.
- Variants: label-only (self-explanatory action) | icon+label (recommended for primary CTAs) | icon-only (limited space + universal icon).

### Segmented Button (Desktop only)
Single-select group (like tabs/radio). Height 40px | pad 10v/16h | gap 8px | typography 12/600 (Label Medium/SemiBold) | radius 12px on end corners only. States: Rest | Selected | Hover | Disabled. Max 4 segments. Use for mutually exclusive view switches (List/Grid, Day/Week/Month).

### Do's & Don'ts

| Do | Don't |
|-------|---------|
| One Filled per primary action | Two Filled buttons side by side |
| Match button size to platform | Desktop Large on Mobile |
| Outlined/Text for secondary actions | Filled for destructive or low-importance actions |
| Short, action-oriented labels ("Save", "Confirm") | Vague labels ("Click here", "OK", "Submit") |
| Icon+label on primary CTAs | Icon-only for primary actions with no context |
| Gestor tokens in Gestor/Multilojas contexts | Mixing Red and Gestor on the same screen |

---

## 2. Input

### Overview

Single-line text input across all platforms. Supports labels, helper text, icons, and validation states. Two components: **Input** (single-line) and **Text Field** (multi-line).

### Sizes

| | Desktop | Mobile / Tablet | Totem |
|---|---|---|---|
| Height | 40px | 48px | 68px |
| Padding V / H | 10px / 16px | 12px / 16px | 16px / 12px |
| Padding H (with icon) | 12px | 12px | 12px |
| Radius | `radius/8` | `radius/16` | `radius/16` |
| Icon size | 20px | 20px | 36px |
| Placeholder | 14px / 400 | 16px / 400 | 24px / 400 |
| Placeholder token | `Body Medium` | `Body Large` | `Heading Small` |

### Anatomy

| Element | Size | Weight | Color Variable | Typography Token |
|---|---|---|---|---|
| Label | 16px | 600 | `text/secondary` | `Label Large/Semibold | 600` |
| Placeholder | 14px | 400 | `text/disabled` | `Body Medium/Regular | 400` |
| Active text | 14px | 400 | `text/secondary` | `Body Medium/Regular | 400` |
| Info text | 12px | 400 | `text/tertiary` | `Body Small/Regular | 400` |
| Error text | 12px | 400 | `red/default` | `Body Small/Regular | 400` |

### Styles

- **Outlined** (default) — transparent background, 1px border.
- **Filled** — `surface/fill` background, no border at rest. Border appears on hover/focus/error.

### States — Outlined

| State | Border | Text Color |
|---|---|---|
| Rest | `stroke/strong` | Placeholder `text/disabled` |
| Hover | `text/primary` | Placeholder `text/disabled` |
| Focused | `#016999` | Placeholder `text/disabled` |
| Active | `stroke/strong` | Text `text/secondary` |
| Error | `red/default` | Text `text/secondary` |
| Disabled | `stroke/default` | Placeholder `text/disabled` |
| Read Only | `stroke/default` | Text `text/primary` |

### States — Filled

| State | Background | Border | Text Color |
|---|---|---|---|
| Rest | `surface/fill` | none | Placeholder `text/disabled` |
| Hover | `surface/fill` | `text/primary` | Placeholder `text/disabled` |
| Focused | `surface/fill` | `#016999` | Placeholder `text/disabled` |
| Active | `surface/fill` | none | Text `text/secondary` |
| Error | `surface/fill` | `red/default` | Text `text/secondary` |
| Disabled | `neutral/50` | none | Placeholder `text/disabled` |
| Read Only | `neutral/50` | none | Text `text/primary` |

### Variant Properties

| Property | Options | Default |
|---|---|---|
| State | Rest, Hover, Focused, Error, Disabled, Read Only, Active | Rest |
| Style | Outlined, Filled | Outlined |
| Label | True, False | True |
| Info | True, False | True |
| Placeholder | True, False | True |
| Icon left | True, False | False |
| Icon right | True, False | False |

### Spacing

| Spacing | Value | Token |
|---|---|---|
| Label to Input | 8px | `spacing/8` |
| Input to Info text | 4px | `spacing/4` |
| Icon to Placeholder | 8px | `spacing/8` |
| Between fields | 16px | `spacing/16` |

### Text Field (Multi-line)

Same tokens as Input. Always includes a label.

| Platform | Default Height |
|---|---|
| Desktop | 120px |
| Mobile / Tablet | 140px |
| Totem | 180px |

### Off-Scale Warnings

| Issue | Fix |
|---|---|
| 32px inputs in Gestor | Standardize to 40px (Desktop) |
| Error padding 12px vs 16px | Normalize across all states |

### Guidelines

- Use **Outlined** as default. **Filled** for colored/image backgrounds.
- Minimum **48px** on Mobile, **68px** on Totem.
- Totem uses `radius/16`, not `radius/8`.
- Totem icons are **36px**, Desktop/Mobile are **20px**.
- Always include a **Label** except for search bars.
- Use **Text Field** only for multi-line content.

---

## 3. Dropdown

### Shared Tokens

| Token | Variable / Value |
|---|---|
| Container Fill | `surface/raised` |
| Container Radius | `8` |
| List Item Radius | `4` |
| List Item Height | `40` |
| Font Family | Poppins |
| Text Color (Rest) | `text/secondary` |
| Text Color (Hover) | `text/primary` |
| Hover Fill | `neutral/50` |
| Accent Color | `red/default` |
| Search Border Color | `stroke/strong` |
| Placeholder Color | `text/disabled` |

### Dropdown Containers

#### Simple Dropdown

**Use:** Basic selection list — single item pick from a short list of options.

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Corner Radius | `8` |
| Layout | Vertical |
| Padding | `8` all sides |
| Item Spacing | `0` |
| Shadow 1 | Drop shadow, offset `0,0`, blur `2`, `#000000` 12% |
| Shadow 2 | Drop shadow, offset `0,2`, blur `4`, `#000000` 14% |

**Supports swapping list items to:** Plain text | Radio | Checkbox | Segmented

#### Filter Dropdown

**Use:** Multi-select filtering — searchable checkbox list with a clear/reset action.

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Corner Radius | `8` |
| Layout | Vertical |
| Padding | `8` all sides |
| Item Spacing | `0` |
| Shadow 1 | Drop shadow, offset `0,0`, blur `2`, `#000000` 12% |
| Shadow 2 | Drop shadow, offset `0,2`, blur `4`, `#000000` 14% |

**Children:**

| Element | Detail |
|---|---|
| Search Input | Outlined input, height `40` |
| List Area | Scrollable frame, height `200` |
| Clear Button | Outlined button, stroke `red/default`, radius `8`, label "Limpar" |

#### Search Dropdown

**Use:** Searchable selection — text search to find and pick from a long list.

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Corner Radius | `8` |
| Layout | Vertical |
| Padding | `8` all sides |
| Item Spacing | `0` |
| Shadow 1 | Drop shadow, offset `0,0`, blur `2`, `#000000` 12% |
| Shadow 2 | Drop shadow, offset `0,2`, blur `4`, `#000000` 14% |

#### Scroll Dropdown

**Use:** Scrollable selection — compact searchable list for space-constrained contexts.

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Corner Radius | `8` |
| Layout | Vertical |
| Padding | `8` all sides |
| Item Spacing | `0` |
| Shadow 1 | Drop shadow, offset `0,0`, blur `2`, `#000000` 12% |
| Shadow 2 | Drop shadow, offset `0,2`, blur `4`, `#000000` 14% |

### List Item Variants

#### List (Normal)

**Use:** Plain text option — simple single-select items.

| Property | Value |
|---|---|
| Height | `40` |
| Corner Radius | `4` |
| Padding | `8` all sides |
| Item Spacing | `10` |
| Font | Poppins Regular 14 |
| Line Height | `16.8px` |
| Letter Spacing | `0.1%` |

| State | Fill | Text Color |
|---|---|---|
| Rest | `surface/raised` | `text/secondary` |
| Hover | `neutral/50` | `text/primary` |

#### Radio

**Use:** Single-select with radio indicator — mutually exclusive choices.

| Property | Value |
|---|---|
| Height | `40` |
| Corner Radius | `4` |
| Padding | `8` all sides |
| Item Spacing | `8` |
| Radio Size | `20 x 20` |
| Font | Poppins Regular 14 |
| Line Height | `16.8px` |

| State | Fill | Text Color |
|---|---|---|
| Rest | `surface/raised` | `text/secondary` |

#### Checkbox

**Use:** Multi-select with checkbox — multiple selections allowed.

| Property | Value |
|---|---|
| Height | `40` |
| Corner Radius | `4` |
| Padding | `8` all sides |
| Item Spacing | `8` |
| Checkbox Size | `24 x 24` |
| Font | Poppins Regular 14 |
| Line Height | `16.8px` |

| State | Fill | Text Color |
|---|---|---|
| Rest | `surface/raised` | `text/secondary` |

#### Segmented List

**Use:** Grouped/categorized list — items with a left-edge color indicator for visual grouping.

| Property | Value |
|---|---|
| Height | `40` |
| Corner Radius | `4` |
| Padding | `8` all sides |
| Indicator Bar | `4px` wide, left edge |
| Font | Poppins Regular 14 |
| Line Height | `16.8px` |

| State | Fill | Text Color |
|---|---|---|
| Rest | `surface/raised` | `text/secondary` |

**Variants:** `Property` = Beginning | Middle | End

### Search List (Inline Search Bar)

**Use:** Search input embedded inside dropdown containers.

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Stroke | `stroke/strong` |
| Stroke Weight | `1` |
| Corner Radius | `4` |
| Padding | `8` all sides |
| Item Spacing | `8` |
| Placeholder Color | `text/disabled` |
| Font | Poppins Regular 14 |
| Line Height | `20px` |
| Icons | `search` (left), `close` (right) |

### Clear Button (Footer Action)

**Use:** Reset/clear action at the bottom of Filter and Scroll dropdowns.

| Property | Value |
|---|---|
| Container Fill | `surface/raised` |
| Container Radius | `4` |
| Container Padding | `4` all sides |
| Inner Button Stroke | `red/default` |
| Inner Button Stroke Weight | `1` |
| Inner Button Radius | `8` |
| Inner Button Style | Outlined |

---

## 4. Calendar

### Shared Tokens

| Token | Variable / Value |
|---|---|
| Container Fill | `surface/raised` |
| Container Radius | `8` (mobile: `12`) |
| Mobile Container Stroke | `stroke/subtle` |
| Font Family | Poppins |
| Primary Color (Dashboard) | `red/default` |
| Primary Color (Area do Gestor) | `gestor/default` |
| Text Default | `text/secondary` |
| Text Secondary | `text/tertiary` |
| Disabled Stroke | `stroke/default` |
| Divider Color | `stroke/subtle` |

### Calendar (Popup)

**Use:** Date selection popup — displays a month grid for picking single dates or date ranges.

**Variants:**
- `Type`: Date | 2 Dates | 2 Dates + Time | 2 Dates + Time + Filter | Month | Year
- `Dates selected`: True | False

#### Container

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Corner Radius | `8` |
| Layout | Vertical |
| Padding | `0` |
| Item Spacing | `0` |

#### Header

| Element | Font | Size | Color |
|---|---|---|---|
| Month/Year Label | Poppins Bold | 16 | `red/default` / `gestor/default` |
| Navigation Arrows (icon fill) | — | — | `red/default` / `gestor/default` |
| Divider (stroke) | — | — | `stroke/subtle` |

#### Weekday Row

| Element | Font | Size | Color |
|---|---|---|---|
| Sunday label (D) | Poppins Bold | 14 | `text/tertiary` |
| Weekday labels (S, T, Q, Q, S) | Poppins Bold | 14 | `text/secondary` |

#### Day Cells

**Font:** Poppins Medium 14

| State | Text Color | Background | Shape |
|---|---|---|---|
| Default | `text/secondary` | none | — |
| Outside month | `text/tertiary` | none | — |
| Selected | `text/inverted` | `red/default` / `gestor/default` | Circle (radius 50) |
| In range | `text/inverted` | `red/default` / `gestor/default` | Rectangle (no radius) |
| Range edge | `text/inverted` | `red/default` / `gestor/default` | Circle (radius 50) |

#### Footer

| Element | Font | Size | Color | Other |
|---|---|---|---|---|
| Apply button label | Poppins SemiBold | 14 | `red/default` / `gestor/default` | Outlined style, stroke same as label color, radius `8` |
| Date labels (De / Ate) | Poppins Medium | 11 | `text/secondary` | — |

#### Month Picker

**Use:** Month selection grid — pick a month from a 4x3 grid.

| State | Text Color | Background | Shape |
|---|---|---|---|
| Default | `text/secondary` | none | — |
| Selected | `text/inverted` | `red/default` / `gestor/default` | Pill (radius 38) |
| Year label | `red/default` / `gestor/default` (Poppins Bold 16) | — | — |

#### Year Picker

**Use:** Year selection grid — pick a year from a grid.

| State | Text Color | Background | Shape |
|---|---|---|---|
| Default | `text/secondary` | none | — |
| Selected | `text/inverted` | `red/default` / `gestor/default` | Pill (radius 38) |

#### Filter Sidebar

**Use:** Quick date range shortcuts — appears on the left side of the calendar in the `+ Filter` variant.

| Property | Value |
|---|---|
| Border right | `stroke/subtle` |
| Padding | `16` |
| Item spacing | `24` |
| Font | Poppins Medium 14 |
| Text color | `text/secondary` |
| Labels | Hoje | Ontem | Essa semana | Semana anterior | Esse Mes | Mes Anterior |

### Calendar Input

**Use:** Date input field — trigger for opening the calendar popup.

**Variants:**
- `Label`: True | False
- `Info`: True | False
- `Type`: Date | 2 Dates | 2 Dates + Time | Month | Year
- `Disabled`: True | False

#### Input Field

| Property | Value |
|---|---|
| Height | `40` |
| Fill | `surface/raised` |
| Corner Radius | `8` |
| Icon | `event_available` |
| Layout | Horizontal |

#### Input States

| State | Stroke |
|---|---|
| Enabled (Dashboard) | `red/default` |
| Enabled (Area do Gestor) | `gestor/default` |
| Disabled | `stroke/default` |

#### Label

| Property | Value |
|---|---|
| Font | Poppins |
| Color | `text/secondary` |

#### Wrapper

| Property | Value |
|---|---|
| Layout | Vertical |
| Spacing | `8` |

### Detached Calendar Frames

| Name | Use | Size | Fill | Radius |
|---|---|---|---|---|
| Calendario default com opcao de filtrar por intervalo | Calendar with optional date range filter toggle | 403 x 476 | `surface/raised` | `8` |
| Calendario com filtro por intervalo | Calendar with active date range filter — expanded view | 403 x 577 | `surface/raised` | `8` |