# Takeat UI Kit — Foundations

Source of truth for building Takeat product interfaces. Whenever there's a choice between an ad-hoc value and an official token, use the token.

**Global rules:**
- Prioritize palette colors. For minor adjustments, modify **opacity only**. New variations follow each family's rules.
- **Poppins** is the sole typeface. Never use sizes or families outside the tokens.
- Spacing, grid, and radius follow a fixed scale (8pt base). Never design outside the grid.
- Dark mode is supported via the `Colors` variable collection (Light/Dark modes). Semantic tokens (`surface/*`, `text/*`, `stroke/*`, `brand/*`, `shadow/*`) remap automatically per mode. Color family primitives (`red/*`, `teal/*`, `neutral/*`, etc.) currently share the same values across both modes — the semantic layer handles the mode-switching.

# Brand Assets

## Takeat Logo

The Takeat logo is an official brand asset and must always be used from the SVG files provided in this repository.

### Full Logo

Use the full Takeat logo when the brand name should be explicitly displayed.

- **Light backgrounds:** `assets/takeat-logo.svg`
- **Dark backgrounds:** `assets/takeat-logo-white.svg`

### Takeat Icon

Use the Takeat icon when the brand needs to be represented without the full wordmark, such as in compact spaces or where the full logo is not appropriate.

- **Light backgrounds:** `assets/takeat-icon.svg`
- **Dark backgrounds:** `assets/takeat-icon-white.svg`

## Asset Usage Rules

- Use only the official Takeat SVG assets provided in this repository.
- Do not redraw, recreate, approximate, or generate a new version of the Takeat logo or icon.
- Do not replace the official logo or icon with text, a different font, or a visually similar symbol.
- Do not change the colors of the official assets.
- Do not apply gradients, outlines, shadows, glows, filters, or other visual effects to the logo or icon.
- Do not distort, stretch, rotate, skew, crop, or otherwise alter the proportions of the assets.
- Preserve the original aspect ratio of the logo and icon.
- Use the standard Takeat logo and icon on light backgrounds.
- Use the white Takeat logo and icon on dark backgrounds when required to maintain sufficient contrast.
- Do not use the white versions on light backgrounds when the standard versions provide sufficient contrast.
- When the full brand identity is required, prefer the full logo over the icon.
- Use the icon only when the available space or context makes the full logo inappropriate.
- Always ensure sufficient contrast between the asset and its background.

## AI Instructions

When generating or modifying a Takeat interface:

- Use the official SVG assets whenever the Takeat logo or icon is required.
- Do not generate the Takeat logo or icon using an image generation model.
- Do not recreate the logo or icon using HTML, CSS, text, or another vector shape when the official asset is available.
- Select the appropriate asset based on the background:
  - Light background → standard asset
  - Dark background → white asset
- If an official asset is available for the required use case, always use it instead of creating a new variation.

---

## 1. Colors

All colors are managed as **Figma variables** in the `Colors` collection, with **Light** and **Dark** modes. Use variable tokens instead of raw hex values whenever possible.

### Rules by tier
- **Standard**: used across Dashboard, Garçom Manager, Garçom Digital, Clube, Totem, etc.
- **Secondary**: used in Area do Gestor and Multilojas — the standard palette applies, **except the primary red, which is replaced by Gestor (Rosa Vinho / Rose)**.
- **Tertiary**: only for details or cases where no standard color fits. Apply sparingly.
- Avoid pure black (`#000000`) in UI elements.

### Semantic Tokens

Semantic tokens map to different raw values depending on the active mode (Light / Dark). Always use semantic tokens for surfaces, text, strokes, and brand elements — they switch automatically when the mode changes.

#### Surface

| Variable | Light | Dark | Use |
|----------|-------|------|-----|
| `surface/background` | `#F6F6F6` | `#121212` | Primary page/screen background — the base layout canvas |
| `surface/raised` | `#FFFFFF` | `#1E1E1E` | Card surfaces, modal backgrounds, input fields — elevated above background |
| `surface/nested` | `#F6F6F6` | `#262626` | Nested containers within raised surfaces (e.g. input inside a card) |
| `surface/fill` | `#EDEDED` | `#2A2A2A` | Filled input backgrounds, disabled surfaces, subtle fills |

#### Text

Dark mode text is white at varying opacity, not a flat color — this is what creates the text hierarchy on dark surfaces (primary reads strongest, disabled reads faintest).

| Variable | Light | Dark | Use |
|----------|-------|------|-----|
| `text/primary` | `#222222` | `#FFFFFF` · 92% | Primary data values (monetary amounts, percentages, headings); icon vectors/paths |
| `text/secondary` | `#545454` | `#FFFFFF` · 64% | **Primary nav labels & body text** — the most used text color in Dashboard |
| `text/tertiary` | `#7A7A7A` | `#FFFFFF` · 38% | Metadata & caption text (phone numbers, restaurant names, secondary labels) |
| `text/disabled` | `#C6C6C6` | `#FFFFFF` · 30% | Disabled text on all button styles and inactive elements |
| `text/inverted` | `#FFFFFF` | `#FFFFFF` · 100% | Text on dark/colored backgrounds (e.g. label on Filled buttons) |

#### Stroke

Dark mode strokes are white at varying opacity, not a flat color — same principle as Text above.

| Variable | Light | Dark | Use |
|----------|-------|------|-----|
| `stroke/subtle` | `#EDEDED` | `#FFFFFF` · 12% | Section dividers, full-width divider lines |
| `stroke/default` | `#C6C6C6` | `#FFFFFF` · 16% | Input borders, separators, skeleton placeholders, disabled element borders |
| `stroke/strong` | `#7A7A7A` | `#FFFFFF` · 24% | Default input border at rest; stronger separators |

#### Brand

| Variable | Light | Dark | Use |
|----------|-------|------|-----|
| `brand/logo` | `#C8131B` | `#FFFFFF` | Brand logo mark |
| `brand/logo-gestor` | `#A82743` | `#FFFFFF` | Gestor brand logo mark |
| `brand/text-secondary` | `#545454` | `#FFFFFF` | Secondary text paired with brand marks |

#### Shadow

Dark mode shadows composite at significantly higher opacity than Light — required for elevation to stay legible on dark surfaces. See the mode-aware `box-shadow` recipes in §3.

| Variable | Light | Dark | Use |
|----------|-------|------|-----|
| `shadow/ambient` | `#000000` · 12% | `#000000` · 40% | Ambient shadow layer (composited at low opacity) |
| `shadow/key-sm` | `#000000` · 14% | `#000000` · 45% | Small key-light shadow — drives `shadow/01`–`02` |
| `shadow/key-lg` | `#000000` · 14% | `#000000` · 50% | Large key-light shadow — drives `shadow/03`–`04` |
| `shadow/key-2xl` | `#000000` · 14% | `#000000` · 55% | Extra-large key-light shadow — drives `shadow/05` |
| `shadow/highlight` | `#FFFFFF` · 0% (off) | `#FFFFFF` · 6% | Subtle top-edge highlight for elevated surfaces — Dark mode only |

#### Scrim

| Variable | Light | Dark | Use |
|----------|-------|------|-----|
| `scrim` | `#000000` · 20% | `#000000` · 20% | Modal/overlay backdrop |

### Color Families

Each color family exposes a consistent set of variable tokens: `default`, `tint`, `40`, `60`, `80`, and `dark`. `tint`, `40`, `60`, and `80` are **the same base hex as `default`, only at reduced opacity** — `tint` = 10%, `40` = 40%, `60` = 60%, `80` = 80%, `default` = 100%. They are not separate colors, so don't approximate them with a different hex. `dark` is the one token with its own distinct (darker) hex, always at 100% opacity, used for pressed/active states. This pattern holds for all seven families below and is identical across Light and Dark modes.

#### Vermelho Takeat — Red (Primary)
Primary brand color. Active navigation, primary CTAs, brand surfaces, and operational status indicators.

| Variable | HEX | Use |
|----------|-----|-----|
| `red/default` | `#C8131B` | **Active nav items (Operacao, Delivery); primary CTAs; brand cover; cancel button fills; table/mesa borders in active state** |
| `red/tint` | `#C8131B` | Light tint for backgrounds, badges, and tag surfaces |
| `red/40` | `#C8131B` | 40% weight — outlined error states, mid-weight badges |
| `red/60` | `#C8131B` | 60% weight — hover/focus accent on primary elements |
| `red/80` | `#C8131B` | 80% weight — stronger accent, bordered error components |
| `red/dark` | `#94090F` | Pressed/active state of primary buttons; high-contrast error text |

#### Verde / Teal (Standard)
Device/connection status, available table states, export actions, positive financial values, chart series, positive action buttons.

| Variable | HEX | Use |
|----------|-----|-----|
| `teal/default` | `#2EC9B7` | **"Conectado" (connected) status; available mesa fill; "Baixar planilha" (export) text/icon; positive action buttons ("Fechar", "Pronto"); download button outline** |
| `teal/tint` | `#2EC9B7` | Light tint for positive metric surfaces, badge backgrounds |
| `teal/40` | `#2EC9B7` | 40% weight — light success badge, strokes |
| `teal/60` | `#2EC9B7` | 60% weight — chart/graph data series, mid-weight fill |
| `teal/80` | `#2EC9B7` | 80% weight — chart series accent, progress indicators |
| `teal/dark` | `#1D9688` | Positive revenue value text; chart series; positive metric card border |

#### Azul / Blue (Standard)
Informational states. "Em andamento" badges, info banners, hyperlinks, notifications, focused input/link states.

| Variable | HEX | Use |
|----------|-----|-----|
| `blue/default` | `#01AFFF` | **Info/secondary buttons; info icon fills** |
| `blue/tint` | `#01AFFF` | Light tint for info surfaces, badge backgrounds |
| `blue/40` | `#01AFFF` | 40% weight — banner border/outline |
| `blue/60` | `#01AFFF` | 60% weight — mid-weight info accent |
| `blue/80` | `#01AFFF` | 80% weight — secondary info interactive accent |
| `blue/dark` | `#018CCC` | Hyperlink text (rest, hover, focus); external link icon; hyperlink underline |

#### Amarelo / Yellow (Standard)
Secondary/detail actions and pending states in the Dashboard (e.g. "Botao Detalhes").

| Variable | HEX | Use |
|----------|-----|-----|
| `yellow/default` | `#FFB32F` | **"Botao Detalhes" (secondary detail actions); pending order status; warning icons; status ellipses on operational screens** |
| `yellow/tint` | `#FFB32F` | Light tint for warning/pending surfaces |
| `yellow/40` | `#FFB32F` | 40% weight — light pending indicator |
| `yellow/60` | `#FFB32F` | 60% weight — attention chip, mid-weight pending state |
| `yellow/80` | `#FFB32F` | 80% weight — mid-light warning tag |
| `yellow/dark` | `#CC8C1D` | Pressed warning state; darkest warning accent |

#### Area do Gestor — Rosa Vinho / Gestor (Secondary)
Primary brand color for the Gestor product. Replaces red in Area do Gestor and Multilojas. Cover, sidebar brand accent, operational buttons, nav text, button outlines.

| Variable | HEX | Use |
|----------|-----|-----|
| `gestor/default` | `#A82743` | **Gestor brand cover; operational buttons; nav text ("Area do Gestor", "Sair"); outlined button borders; active brand elements** |
| `gestor/tint` | `#A82743` | Light tint for brand surfaces, badge backgrounds |
| `gestor/40` | `#A82743` | 40% weight — disabled/secondary brand tags |
| `gestor/60` | `#A82743` | 60% weight — mid-light brand indicator |
| `gestor/80` | `#A82743` | 80% weight — bordered brand elements, hover accents |
| `gestor/dark` | `#75162B` | Pressed/active state of brand buttons; darkest brand accent |

#### Laranja / Orange (Tertiary)
Decorative accents and edge cases. **Never** for status or primary actions.

| Variable | HEX | Use |
|----------|-----|-----|
| `orange/default` | `#FF7D24` | **Decorative elements, special promotional indicators** |
| `orange/tint` | `#FF7D24` | Light tint for decorative backgrounds |
| `orange/40` | `#FF7D24` | 40% weight — light decorative tags |
| `orange/60` | `#FF7D24` | 60% weight — illustration accents |
| `orange/80` | `#FF7D24` | 80% weight — UI detail highlights |
| `orange/dark` | `#CC5F14` | Pressed / high-contrast detail; darkest accent |

#### Verde 2 / Green (Tertiary)
Financial & KPI contexts — upward-trending metrics, net totals, positive growth. Distinct from Teal, which is operational status; Green is business performance.

| Variable | HEX | Use |
|----------|-----|-----|
| `green/default` | `#27A84C` | **Confirmation/approval buttons in Dashboard flows; positive action fill** |
| `green/tint` | `#27A84C` | Light tint for positive metric surfaces |
| `green/40` | `#27A84C` | 40% weight — light positive metric tag |
| `green/60` | `#27A84C` | 60% weight — mid-light positive indicator |
| `green/80` | `#27A84C` | 80% weight — mid-weight positive accent |
| `green/dark` | `#167532` | "TrendingUp" icon (positive KPI arrow); positive revenue text; "Total Liquido" card border; pressed positive state |

### Neutral Colors (Primitives)
The structural backbone — raw neutral values referenced by semantic tokens and used directly when no semantic token applies.

| Variable | HEX | Use |
|----------|-----|-----|
| `neutral/white` | `#FFFFFF` | Card surfaces, modal backgrounds, input fields, text on dark/colored backgrounds — the most used color |
| `neutral/50` | `#F6F6F6` | Primary page/screen background — the base layout canvas |
| `neutral/100` | `#EDEDED` | Section dividers, full-width divider lines |
| `neutral/200` | `#C6C6C6` | Input borders, separators, skeleton placeholders, disabled element borders |
| `neutral/500` | `#7A7A7A` | Metadata & caption text (phone numbers, restaurant names, secondary labels); default input border |
| `neutral/700` | `#545454` | **Primary nav labels & body text** — the most used text color in Dashboard |
| `neutral/900` | `#222222` | Primary data values (monetary amounts, percentages, headings); icon vectors/paths |
| `neutral/black` | `#000000` | Icon vectors and external brand/payment logos only — never UI text or large backgrounds |

---

## 2. Typography

**Poppins** is the only family. Always apply official tokens; never invent sizes.

### Body vs. Label
- **Body** — extended, flowing text: descriptions, paragraphs, multi-line content.
- **Label** — short, interactive, or contextual text: buttons, tags, chips, table headers, input labels, badges, metadata, nav items.

Apply this distinction at every size level before choosing a token.

### Text style tokens

| Token | Size | LH | LS | Weights & use |
|-------|------|----|----|---------------|
| **Details** | 8px | 12px | 0 | Desktop only. 500: micro-labels in tight spaces; 600: nav module labels below icons; 700: high-emphasis micro-tags ("ON"/"OFF"), check contrast |
| **Label Small** | 11px | 16px | 0.5px | Desktop & Mobile (restricted), never Totem. 500: comparison chips ("vs. previous period"); 600: bottom-nav sub-labels on Mobile, price footnotes; 800: high-emphasis short labels in banners (use sparingly) |
| **Body Small** | 12px | 16px | 0.4px | Desktop & Mobile. Extended secondary text. 400: secondary/status text; 500: insight paragraphs, legends (most used body on desktop); 600: secondary text with emphasis |
| **Label Medium** | 12px | 16px | 0.5px | Desktop & Mobile. Short labels/identifiers. 500: bottom-nav tabs on Mobile; 600: timestamps, IDs, operator names, metadata; 700: table column headers |
| **Body Medium** | 14px | 20px | 0.25px | Desktop & Mobile / Totem (caution). **Primary body size.** 400: nav items, lists, table rows; 500: **most used style in the system** — button labels & interactive text; 600: section/tab labels, entity names |
| **Label Large** | 14px | 20px | 0.1px | Desktop & Mobile / Totem (caution). Short interactive labels. 400: placeholders; 500: KPI labels, form fields; 600: percentage/metric labels, action links, Mobile primary CTA; 700: active nav states, download/export labels |
| **Body Large** | 16px | 24px | 0.5px | All platforms (smallest body for Totem). 400: item/product descriptions; 500: modal/drawer paragraphs; 600: prices/values in blocks, grouping labels |
| **Title Small** | 16px | 24px | 0.15px | All / Totem (caution). 400: supporting text; 500: modal subsection content; 600: monetary values, input titles; 700: section/modal headers, primary CTA |
| **Title Medium** | 18px | 24px | 0 | All. 400: supporting text; 500: large form labels, Totem search placeholder; 600: drawer/modal titles (standard for overlays); 700: report section headings, product names on Totem |
| **Title Large** | 22px | 28px | 0 | Desktop & Totem, never Mobile. 400: large numeric display (table numbers); 500: ranking indicators; 600: order identifiers, mid-tier KPIs; 700: chart/report titles, module headings |
| **Heading XS** | 20px | 28px | 0 | Desktop & Totem (restricted), never Mobile. 400/500: numeric display & KPI counters; 600: emphasized KPIs; 700: primary section headings |
| **Heading Small** | 24px | 32px | 0 | Desktop & Totem only. Largest financial/data value on desktop. 400: supporting numeric; 500: primary metric; 600: main revenue/performance; 700: headline metric |
| **Heading Medium** | 28px | 36px | 0 | Desktop & Totem, never Mobile. 400: supporting; 500: Totem nav button labels; 600: emphasized page titles; 700: page headers & entity names on desktop |
| **Heading Large** | 32px | 40px | 0 | Totem only. Menu section titles, categories — uppercase, high contrast. 700: primary titles (uppercase) |
| **Display** | 40px | 48px | 0 | Totem only. Hero/splash — largest type in the system |

### Weight reference

| Weight | Role |
|--------|------|
| 400 — Regular | Flowing body, placeholders, table data, chart values — passive reading |
| 500 — Medium | Default interactive weight — buttons, labels, form, nav |
| 600 — SemiBold | Values, prices, timestamps, links, tabs — moderate emphasis |
| 700 — Bold | Titles, active states, CTAs, headers — strong emphasis |
| 800 — ExtraBold | Rare — only the Label Small token in specific highlights |

### Platform per token

| Token | Size | Desktop | Mobile | Totem |
|-------|------|:---:|:---:|:---:|
| Details | 8px | Yes | No | No |
| Label Small | 11px | Yes | Caution | No |
| Body Small | 12px | Yes | Yes | No |
| Label Medium | 12px | Yes | Yes | No |
| Body Medium | 14px | Yes | Yes | Caution |
| Label Large | 14px | Yes | Yes | Caution |
| Body Large | 16px | Yes | Yes | Yes |
| Title Small | 16px | Yes | Yes | Yes |
| Title Medium | 18px | Yes | Yes | Yes |
| Title Large | 22px | Yes | No | Yes |
| Heading XS | 20px | Yes | No | Caution |
| Heading Small | 24px | Yes | No | No |
| Heading Medium | 28px | Yes | No | Yes |
| Heading Large | 32px | No | No | Yes |
| Display | 40px | No | No | Yes |

---

## 3. Spacing, Grids & Radius

### Spacing (8pt base)
Every value is a multiple or subdivision of 8. Controls internal padding and gaps.

| Token | Value | Use |
|-------|-------|-----|
| `spacing/2` | 2px | Hairline — tight inline, icon-to-text within a label |
| `spacing/4` | 4px | Extra tight — icon and label, stacked chips |
| `spacing/8` | 8px | **Default gap** — the most used; items in lists, rows, auto-layout |
| `spacing/12` | 12px | Comfortable — vertical groups, compact card padding |
| `spacing/16` | 16px | Standard padding — cards, modals, list items, section containers |
| `spacing/24` | 24px | Generous — section padding, distinct blocks, modal interior |
| `spacing/32` | 32px | Large — between major sections on desktop |
| `spacing/40` | 40px | Extra large — between top-level areas; outer padding on Totem |

**Platform:** `2` (D/M) | `4` (D/M/T) | `8` (D/M/T) | `12` (D/M) | `16` (D/M/T) | `24` (D/M/T) | `32` (Desktop) | `40` (Desktop/Totem)

**Common patterns:**

| Context | Padding | Gap |
|---------|---------|-----|
| Chip/badge | 4px v / 8px h | — |
| Compact button | 8px v / 12px h | 8px |
| Default button | 12px v / 16px h | 8px |
| Input | 12px v / 16px h | — |
| Compact card | 12px | 8px between rows |
| Default card | 16px | 12px between rows |
| Modal/drawer | 24px | 16px between sections |
| Page section | 24-32px | 24px between blocks |
| Totem screen | 40px outer margin | 24px between elements |

> Off-scale values found in existing files: 10, 13, 20, 21, 25px. Map to the nearest token (10->8 or 12, 13->12, 20->16 or 24, 21->24, 25->24).

### Grids
Never design outside the grid.

**Desktop** — 12 columns | 16px gutter | 16-20px margin | min width 1024px. Applies to Dashboard and Gestor.
Combinations: 12 (full) | 6+6 | 8+4 (main+sidebar) | 4+4+4 | 3+3+3+3 (cards).

**Mobile** — 4 columns | 16-20px gutter | 16-20px margin | target width 390px.
Combinations: 4 (full) | 2+2 (pairs/buttons).

**Totem** — 5 columns | 20px gutter | 40px margin | target width 1080px (portrait kiosk). Wider margin for the physical bezel and touch distance.
Combinations: 5 (nav/CTA) | 2-3 cards per row | 5 (category tabs).

### Border Radius

| Token | Value | Use |
|-------|-------|-----|
| `radius/8` | 8px | Subtle — inputs, table rows, tooltips, small chips |
| `radius/12` | 12px | **Default** — the most used; cards, buttons, dropdowns, modals |
| `radius/16` | 16px | Medium — larger cards, bottom sheets, floating panels, Mobile cards |
| `radius/24` | 24px | Strong — prominent cards, Mobile modals, Totem product cards |
| `radius/32` | 32px | Very rounded — large panels, hero cards, decorative containers |
| pill (100px+) | 9999px / 50% | Avatars, toggles, status dots, icon containers (not a token) |

**Platform:** `4` (D / M-caution / no-Totem) | `8` (D/M/T) | `12` (D/M/T) | `16` (D/M/T) | `24` (D/T / no-M) | pill (D/M/T)

### Shadows (elevation)
Elevation scale from 01 (lowest) to 05 (highest). Each level composites two layers — a tight **key-light** shadow and a soft **ambient** shadow — resolved from the `shadow/*` semantic tokens (§1). Use `02` as the default; `01` for small items and components needing emphasis; `03`-`05` for larger components.

**Dark mode composites at much higher opacity than Light** (ambient 40% vs 12%; key-light 45–55% vs 14%) — always resolve elevation through the semantic tokens rather than hardcoding Light's alpha values, or shadows will be nearly invisible on dark surfaces.

**Light mode**

| Token | Use | box-shadow (CSS) |
|-------|-----|------------------|
| `shadow/01` | Small items / components needing emphasis | `0 1px 2px rgba(0,0,0,.14), 0 0 2px rgba(0,0,0,.12)` |
| `shadow/02` | **Default** — most items | `0 2px 4px rgba(0,0,0,.14), 0 0 2px rgba(0,0,0,.12)` |
| `shadow/03` | Bigger components | `0 4px 8px rgba(0,0,0,.14), 0 0 2px rgba(0,0,0,.12)` |
| `shadow/04` | Bigger components | `0 8px 16px rgba(0,0,0,.14), 0 0 2px rgba(0,0,0,.12)` |
| `shadow/05` | Highest elevation | `0 10px 25px rgba(0,0,0,.14), 0 0 8px rgba(0,0,0,.12)` |

**Dark mode**

| Token | Use | box-shadow (CSS) |
|-------|-----|------------------|
| `shadow/01` | Small items / components needing emphasis | `0 1px 2px rgba(0,0,0,.45), 0 0 2px rgba(0,0,0,.40)` |
| `shadow/02` | **Default** — most items | `0 2px 4px rgba(0,0,0,.45), 0 0 2px rgba(0,0,0,.40)` |
| `shadow/03` | Bigger components | `0 4px 8px rgba(0,0,0,.50), 0 0 2px rgba(0,0,0,.40)` |
| `shadow/04` | Bigger components | `0 8px 16px rgba(0,0,0,.50), 0 0 2px rgba(0,0,0,.40)` |
| `shadow/05` | Highest elevation | `0 10px 25px rgba(0,0,0,.55), 0 0 8px rgba(0,0,0,.40)` |

> Optional: on prominent Dark-mode surfaces (modals, cards) pair elevation with a top-edge highlight — `inset 0 1px 0 rgba(255,255,255,.06)` (`shadow/highlight`) — to reinforce the light-source cue. Not used in Light mode, where `shadow/highlight` is fully transparent.
