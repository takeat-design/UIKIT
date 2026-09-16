# Takeat UI Kit — Components

Component specifications for Takeat product interfaces. All components use Poppins and reference foundation tokens defined in `foundations.md`. Color references use the `Colors` variable collection (Light/Dark modes) — prefer semantic tokens (`text/*`, `surface/*`, `stroke/*`) and color family tokens (`red/*`, `teal/*`, `gestor/*`, etc.) over raw hex values.

---

## 1. Buttons

**Anatomy:** Icon (optional, scales with the button) | Label (typography token for the size) | Container (clickable surface with padding, radius, fill).

### Sizes
Never mix sizes across platforms.

| Size | Height | Pad V | Pad H | Radius | Typography | Icon | Icon-only | Platform |
|------|--------|-------|-------|--------|-----------|------|-----------|----------|
| Small | 24px | 4px | 8px | 8px | 12/600 (Body Small/SemiBold) | 16px | 24x24 | Desktop |
| Medium | 32px | 10px | 16px | 12px | 14/600 (Label Large/SemiBold) | 20px | 32x32 | Desktop |
| Large | 40px | 8px | 16px (24px label-only) | 12px | 14/600 (Label Large/SemiBold) | 24px | 40x40 | Desktop |
| Mobile/Tablet | 48px | 12px | 16px (24px label-only) | 16px | 16/600 (Title Small/SemiBold) | 24px | 48x48 | Mobile |
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
| Radius | `radius/12` | `radius/16` | `radius/16` |
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
| Disabled | `stroke/medium` | Placeholder `text/disabled` |
| Read Only | `stroke/medium` | Text `text/primary` |

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
| Mobile Container Stroke | `stroke/default` |
| Font Family | Poppins |
| Primary Color (Dashboard) | `red/default` |
| Primary Color (Area do Gestor) | `gestor/default` |
| Text Default | `text/secondary` |
| Text Secondary | `text/tertiary` |
| Disabled Stroke | `stroke/medium` |
| Divider Color | `stroke/default` |

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
| Divider (stroke) | — | — | `stroke/default` |

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
| Border right | `stroke/default` |
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
| Disabled | `stroke/medium` |

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

---

## 5. Table

### Overview

Modular data table for Desktop. Every piece is independent and can be combined freely — there are no fixed variants. The final composition depends on the context. Column headers and table body are always present. Pagination is required only when the table has more than 10 rows.

**Required:** Column Headers | Table Body | Export Button | Pagination (only when > 10 rows)
**Optional:** Toolbar elements (title, subtitle, search, filter button, additional buttons) | Active Filters | Header Groups | Expandable Row | Total Row | Checkbox Column | Actions Column | Selection Bar | Cell subtitle | Cell chip

### Anatomy

Vertical stack, top to bottom:

| Order | Section | Required | Height |
|---|---|---|---|
| 1 | Toolbar | No | 72px |
| 2 | Active Filters | No | 44px (+ 2px divider) |
| 3 | Header Groups | No | 32px |
| 4 | Column Headers | Yes | 48px |
| 4.1 | Total Row | No | 48px, first body row |
| 5 | Table Body | Yes | min 44px per row |
| 6 | Pagination | When > 10 rows | 64px |
| — | Selection Bar | No | 48px, floating over Pagination |

### Container

The table always sits inside a white card. Two nested layers:

```
┌ Card ─────────────────────────────────┐  surface/raised · stroke/default · padding 16
│ ┌ Table Frame ──────────────────────┐ │  stroke/medium
│ │ Toolbar                           │ │
│ │ Header Groups · Column Headers    │ │
│ │ Body                              │ │
│ │ Pagination                        │ │
│ └───────────────────────────────────┘ │
└───────────────────────────────────────┘
```

#### Card (outer)

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Stroke | `stroke/default`, 1px |
| Corner Radius | `radius/16` |
| Padding | `spacing/16` all sides |
| Width | Fill — follows the screen |

#### Table Frame (inner)

| Property | Value |
|---|---|
| Fill | `surface/raised` |
| Stroke | `stroke/medium`, 1px (external border) |
| Internal dividers | `stroke/medium`, 0.5px — last row has no bottom border |
| Corner Radius | `radius/16`, content clipped to the radius |
| Layout | Vertical |
| Padding | `0` — each section (Toolbar, Pagination, cells) carries its own padding |
| Width | Fill — the Card's content width |

### Toolbar

**Use:** Top bar with any combination of title, search, and actions. All elements are optional.

| Property | Value |
|---|---|
| Height | `72` |
| Layout | Horizontal, space-between, center aligned |
| Padding | `spacing/16` all sides |
| Action group gap | `spacing/8` |

| Element | Detail | Color | Typography Token |
|---|---|---|---|
| Title | Left side | `text/primary` | `Title Small/SemiBold | 600` |
| Subtitle | Below title | `text/secondary` | `Body Medium/Regular | 400` |
| Search Input | Input (search), icon `Search`, placeholder "Buscar na tabela", 210 x 40 | See Input (§2) | `Body Medium/Regular | 400` |
| Filter Button | Outlined, Large (40px), icon `FilterList`, label "Filtros". Can show count ("Filtros • 2"). Can be replaced by Calendar Input (§4), Dropdown (§3), etc. | Brand (`red/*` / `gestor/*`) | See Buttons (§1) |
| Export Button | **Required.** Outlined, Large (40px), icon `ExportFile`, label "Exportar". PDF always; CSV only when requested | `teal/default` | See Buttons (§1) |
| Additional Buttons | Any quantity. Same style and size as Filter Button (Outlined, Large) | Brand (`red/*` / `gestor/*`) | See Buttons (§1) |

### Active Filters

**Use:** Shows applied filters below the toolbar. Only rendered when at least one filter is active.

| Element | Detail | Color | Typography Token |
|---|---|---|---|
| Divider | 2px, full width | `stroke/default` | — |
| Row | Vertical, height `44`, padding `8` top/bottom | — | — |
| Label | "Filtros aplicados:" | `text/secondary` | `Body Small/Regular | 400` |
| Chips | Horizontal, gap `spacing/8`, no quantity limit | — | — |
| Filter Chip | Removable, height `24`, label "nome do filtro: valor", icon `Close` | — | `Label Medium` |

### Header Groups

**Use:** Groups two or more columns under a shared label. No quantity limit.

| Property | Value |
|---|---|
| Height | `32` |
| Fill | `surface/nested` (#F6F6F6) |
| Layout | Horizontal |
| Span | 1 or more columns |
| Text | Uppercase, `text/secondary`, `Label Medium/Medium | 500` (12/500) |

### Column Headers

| Property | Value |
|---|---|
| Height | `48` |
| Fill | `surface/fill` (#EDEDED) |
| Layout | Horizontal, center aligned |
| Label to Sort gap | `spacing/4` |
| Label | `text/secondary`, `Label Large/SemiBold | 600` |
| Sort icon | `Exchange`, 16px, optional per column |
| Sub-columns | Optional. Each sub-column has its own header and optional sort |

### Table Body

| Property | Value |
|---|---|
| Layout | Horizontal (columns stacked vertically) |
| Row min height | `44` |
| Cell padding H | `spacing/12` |
| Row divider | Bottom, 0.5px, `stroke/medium` |
| Text | `text/secondary`, `Body Medium/Medium | 500` (14/500) |
| Overflow | `text-overflow: ellipsis` — avoid horizontal scroll (see Column Width) |

#### Row Heights

| Content | Height |
|---|---|
| Plain text | 44px (min) |
| Text + subtitle | 62px |
| Text + chip | ~49px |
| Custom | Variable (min 44px) |

#### Cell Content

Free, context-dependent. No type restriction.

| Type | Detail | Increases row height |
|---|---|---|
| Text | Plain text | No |
| Text + Subtitle | Main text + subtitle below (`text/tertiary`, `Body Small/Regular | 400`) | Yes |
| Text + Chip | Text + chip/badge beside or below | Yes |
| Chip | Standalone status chip | No |
| Input | Editable Input (§2) | Depends |
| Button | Action button, Small size (§1) | No |
| Icon | Standalone icon | No |
| Custom | Any other component | Depends |

#### Column Width

- Proportional to cell content; total width follows the screen.
- Numeric columns tend to be narrower.
- Long-text columns get width proportional to content.
- Actions column has a fixed minimum width that fits its buttons.
- If the table doesn't fit, truncate text first, then narrow numeric columns, then drop secondary columns.
- **Horizontal scroll only as a last resort**, when the table has too many columns. In that case the identity column is pinned left and the actions column pinned right.

### Expandable Row

**Use:** Reveals extra content below a row.

| Property | Value |
|---|---|
| Trigger | `ChevronRight`, 16px, first column |
| Behavior | Rotates 90° on expand |
| Icon color | `text/secondary` |
| Expanded content | Free — cards, nested tables, details, forms, any layout |

### Total Row (Summary)

**Use:** Optional totals/summary row. Always the first row of the body.

| Property | Value |
|---|---|
| Height | `48` |
| Fill | `red/tint` (Dashboard) / `gestor/tint` (Area do Gestor / Multilojas) |
| Text | `text/primary`, `Body Medium/SemiBold | 600` (14/600) |

### Checkbox Column

**Use:** Multi-row selection. Enables the Selection Bar.

| Property | Value |
|---|---|
| Position | Own first column, or inside the identity cell before the chevron. Pick one per table |
| Checkbox size | `24 x 24` |
| States | Unchecked, Checked, Indeterminate |
| Header checkbox | Indeterminate when some rows are selected |

### Actions Column

| Property | Value |
|---|---|
| Position | Last column |
| Header | "Ações" |
| Content | 1 or more buttons per row |

| Action type | Detail |
|---|---|
| Menu Button | `MenuCircles` 24px — opens Simple Dropdown (§3) |
| Icon Button | Icon-only, Small size (§1) — edit, delete, view, etc. Requires tooltip |
| Text Button | Text Button style (§1) |

### Selection Bar

**Use:** Floating bar over Pagination when rows are selected via checkbox. Fully customizable.

| Property | Value |
|---|---|
| Height | `48` |
| Layout | Horizontal, center aligned |
| Gap | `spacing/16` |
| Counter | "{n} selecionados", `text/secondary`, `Body Medium/Regular | 400` |
| Buttons | Max 4, Medium size (32px), gap `spacing/8` |
| Elevation | `shadow/02` |

### Pagination

**Use:** Required when the table has more than 10 rows. Tables with 10 rows or fewer have no pagination.

| Property | Value |
|---|---|
| Height | `64` |
| Layout | Horizontal, space-between |
| Padding | `spacing/16` all sides |
| Controls gap | `spacing/8` |

| Element | Detail | Color / Style | Typography Token |
|---|---|---|---|
| Record Count | "{start}–{end} de {total} registros" | `text/secondary` | `Body Medium/Regular | 400` |
| Rows per page | Select, label "Linhas por página", height `32`, options 10 / 25 / 50 / 100, default 10 | See Dropdown (§3) | `Body Medium/Regular | 400` |
| Previous | `ChevronLeft`, 18px | `text/secondary` | — |
| Page Buttons | 32 x 32 | Active: Filled (brand) · Inactive: Ghost (Text Button) | `Label Large/SemiBold | 600` |
| Next | `ChevronRight`, 18px | `text/secondary` | — |

> **Gestor / Multilojas:** swap `red/*` for `gestor/*` on brand buttons, the active page, and the Total Row fill. Export Button stays `teal/default`.

### Off-Scale Warnings

| Issue | Fix |
|---|---|
| Foundations lists `Label Medium 700` as table column headers | Update Foundations to `Label Large 600` |

### Guidelines

- Avoid horizontal scroll — truncate with ellipsis. Only allow it when the table has too many columns.
- Minimum cell height is **44px**.
- Pagination only when there are **more than 10 rows**; rows per page starts at **10**.
- Export Button is **required**: always **teal**, **PDF** always, **CSV** only when requested.
- Header groups and sort are optional, with no quantity limit.
- Selection Bar has at most **4** Medium buttons.
- Filters are not limited to the Filter Button — Calendar Input, Dropdown, etc. are valid.
- Toolbar buttons (filters, export, additional) are **Large (40px)**; Selection Bar buttons are **Medium (32px)**; row actions are Small.

### Do's & Don'ts

| Do | Don't |
|---|---|
| Truncate long text with ellipsis | Horizontal scroll when truncating would solve it |
| Teal Export Button with PDF | Export in brand color, or CSV without PDF |
| Pagination on tables with more than 10 rows | Pagination on tables with 10 rows or fewer |
| Up to 4 buttons in the Selection Bar | 5+ actions in the Selection Bar |
| Tooltip on icon-only row actions | Icon-only actions with no context |
| Gestor tokens in Gestor/Multilojas | Mixing Red and Gestor on the same table |
