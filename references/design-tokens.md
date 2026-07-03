# Design Tokens — Agent Console UI

All tokens are CSS custom properties defined in `assets/agent-console.css` on `:root`
(light) and overridden by `[data-ac-theme="dark"]`, `[data-ac-accent="…"]` and
`[data-ac-density="compact"]`. Use tokens, never raw hex, in page code.

## 1. Color

### Canvas & surfaces (light theme)

| Token | Value | Use |
|---|---|---|
| `--ac-bg` | `#F4F6F9` | App/page background (cool light gray) |
| `--ac-panel` | `#FFFFFF` | Cards, panes, list rows, bubbles-in |
| `--ac-panel-soft` | `#F7F9FC` | Table headers, hover rows, input backgrounds, nested cards |
| `--ac-panel-sunken` | `#EFF2F7` | Wells, image placeholders, scrollbar track |
| `--ac-border` | `#E7EAF0` | Default 1px borders, dividers |
| `--ac-border-strong` | `#D8DEE8` | Inputs, interactive outlines |
| `--ac-rail` | `#191D26` | Dark icon rail / dark sidebar |
| `--ac-rail-text` | `#8B93A3` | Icons/text on the rail (active: white) |
| `--ac-scrim` | `rgba(23,29,41,.45)` | Modal overlay |

### Text

| Token | Value | Use |
|---|---|---|
| `--ac-text` | `#1F2329` | Primary text, values, titles |
| `--ac-text-2` | `#5F6673` | Secondary text, body in cards |
| `--ac-text-3` | `#9AA3B2` | Muted: meta lines, placeholders, kv labels |
| `--ac-text-invert` | `#FFFFFF` | Text on primary/danger fills |

### Brand / accent (default accent = blue)

| Token | Value | Use |
|---|---|---|
| `--ac-primary` | `#2E6BE6` | THE loud color: outgoing bubbles, primary buttons, links, active states, accent bars |
| `--ac-primary-strong` | `#2456C4` | Hover/pressed of primary |
| `--ac-primary-soft` | `#EAF1FE` | Tinted backgrounds: active chips, blue tags, table header tint |
| `--ac-primary-border` | `#C6D8FA` | Border of soft-blue elements |
| `--ac-primary-soft-text` | `#2E6BE6` | Text on `--ac-primary-soft` |

### Semantic hues (each has `*`, `*-soft`, and text-on-soft is the base color)

| Hue | Base | Soft bg | Meaning in this style |
|---|---|---|---|
| success/green | `--ac-success: #1F9D61` | `--ac-success-soft: #E6F6EE` | quality grades (中质量/高质量), healthy windows, delivered |
| warning/amber | `--ac-warning: #B7791F` | `--ac-warning-soft: #FFF6E3` | paused, human-takeover, expiring |
| danger/red | `--ac-danger: #DE4B4B` | `--ac-danger-soft: #FDEDED` | human follow-up urgency, lost deals, destructive actions |
| gold | `--ac-gold: #A87B2D` | `--ac-gold-soft: #FAF1DC` | high-value customers, premium |
| info/blue | `--ac-primary` | `--ac-primary-soft` | AI-owned states, informational chips |
| neutral | `--ac-text-2` | `--ac-panel-sunken` | default/low-priority tags |

Special: `--ac-whatsapp: #25D366` — only for WhatsApp CTA chips/buttons on creative cards
and contact rows. `--ac-warning-dot: #F0A020` — status dots (amber reads better saturated).

### Avatar palette (deterministic by name hash)

`--ac-avatar-1..6`: `#2E6BE6`, `#E5484D`, `#1F9D61`, `#B58A2E`, `#7C5CD6`, `#0E9BA6`.
White initials, full circle.

## 2. Typography

| Token | Value |
|---|---|
| `--ac-font` | `-apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", "Noto Sans SC", sans-serif` |
| `--ac-mono` | `"SF Mono", ui-monospace, "JetBrains Mono", "Roboto Mono", "Menlo", monospace` |

### Scale (comfortable density)

| Role | Size/line | Weight | Notes |
|---|---|---|---|
| Metric XL | 22px/1.2 mono | 700 | `$90.00`, `675-1800` |
| Metric M | 16px/1.3 mono | 600 | inline stats |
| Page/card title | 16px/1.4 | 600 | pane headers |
| Section title | 14px/1.4 | 600 | with accent bar |
| Body | 13px/1.6 | 400 | default |
| Body strong | 13px | 600 | names, values |
| Secondary | 12px/1.5 | 400 | meta, kv labels, tags |
| Tag text | 12px | 500 | inside pills/tags |

Rules:
- Everything numeric that a user might compare or copy → `--ac-mono` via `.ac-num`
  (money, ranges, phones, IDs, percentages, times like `07:00-23:00`).
- Chinese text never letter-spaced; Latin all-caps never used.
- Links: 13px, `--ac-primary`, no underline, `→` suffix common (`看数据 →`).

## 3. Spacing & sizing

4px base grid. Common steps: 4, 6, 8, 12, 16, 20, 24.

| Token | Comfortable | Compact |
|---|---|---|
| `--ac-pad-card` | 16px | 12px |
| `--ac-pad-pane` | 20px | 14px |
| `--ac-gap` | 12px | 8px |
| `--ac-gap-sm` | 8px | 6px |
| `--ac-row-h` | 36px | 30px (list rows, inputs) |

Pane widths (see layouts.md): rail 56px; list/library pane 280–380px; detail pane 320–360px;
center pane flexible with `min-width: 480px`.

## 4. Radius

| Token | Value | Use |
|---|---|---|
| `--ac-radius-lg` | 14px | outer panels, modal pages |
| `--ac-radius` | 10px | cards, bubbles, banners, inputs |
| `--ac-radius-sm` | 6px | buttons, thumbnails, chips-in-cards |
| `--ac-radius-tag` | 4px | semantic tags |
| `--ac-radius-full` | 999px | filter pills, avatars, count bubbles, status dots |

Chat bubbles: `--ac-radius` on all corners except the corner pointing at the sender,
which is 4px (outgoing: top-right 4px; incoming: top-left 4px).

## 5. Elevation

Borders do the work; shadows are whispers.

| Token | Value | Use |
|---|---|---|
| `--ac-shadow-sm` | `0 1px 2px rgba(23,29,41,.05)` | cards, list hover |
| `--ac-shadow` | `0 4px 16px rgba(23,29,41,.08)` | popovers, dropdowns |
| `--ac-shadow-lg` | `0 12px 40px rgba(23,29,41,.16)` | modal pages |

## 6. Dark theme mapping (`[data-ac-theme="dark"]`)

| Token | Dark value |
|---|---|
| `--ac-bg` | `#12151C` |
| `--ac-panel` | `#1A1E27` |
| `--ac-panel-soft` | `#212633` |
| `--ac-panel-sunken` | `#151922` |
| `--ac-border` | `#2A3040` |
| `--ac-border-strong` | `#39415466` fallback `#394154` |
| `--ac-text` | `#E8EBF1` |
| `--ac-text-2` | `#A6AEBD` |
| `--ac-text-3` | `#6E7789` |
| `--ac-primary` | `#4C82F0` (slightly lifted for contrast) |
| `--ac-primary-soft` | `#20304F` |
| `--ac-primary-border` | `#2E4370` |
| soft hues | tinted dark: success-soft `#173226`, warning-soft `#33290F`, danger-soft `#361D1F`, gold-soft `#322A16` |
| base hues | lifted: success `#3DBE84`, warning `#D9A03F`, danger `#E9686C`, gold `#CFA14E` |
| `--ac-rail` | `#0D1016` |
| shadows | opacity ×2, e.g. `0 1px 2px rgba(0,0,0,.4)` |

Outgoing bubbles stay `--ac-primary` filled; incoming bubbles become `--ac-panel-soft`
with `--ac-border`.

## 7. Accent themes (`[data-ac-accent]`)

Only the primary family changes; semantic hues stay fixed.

| Accent | primary | strong | soft | border | When |
|---|---|---|---|---|---|
| (default) blue | `#2E6BE6` | `#2456C4` | `#EAF1FE` | `#C6D8FA` | general consoles |
| `green` | `#0E9F6E` | `#0B7F58` | `#E4F5EE` | `#B5E2CF` | trade/WhatsApp/commerce ops |
| `violet` | `#6E56CF` | `#5A45AE` | `#EFEBFC` | `#D3C9F2` | analytics/AI-heavy tools |
| `orange` | `#E8730C` | `#C25F09` | `#FDEFE1` | `#F5CFA6` | e-commerce/marketplace |

Dark theme + accent combine: accents also define a `-dark` lift (see stylesheet).

## 8. Motion

Minimal. `--ac-ease: cubic-bezier(.2,.7,.3,1)`, durations 120ms (hover) / 200ms (panels).
Only animate: background-color, border-color, opacity, transform ≤4px. No bouncing,
no skeleton shimmer faster than 1.2s.
