# Layout Archetypes — Agent Console UI

Four page archetypes cover almost everything in this style. All use the same shell
pattern: `body` → `.ac-app` → `.ac-shell` (flex, `height:100vh`) → panes.
Panes are `.ac-pane` (white, right border); the chat/canvas pane uses `.is-canvas`
(gray `--ac-bg`) so white bubbles and cards pop.

## A. Copilot console (3 panes) — e.g. AI campaign builder

```
┌────────────┬──────────────────────────────┬──────────────┐
│ Library    │  Chat / AI answers           │ Live summary │
│ 280–320px  │  flex, min 480px             │ 340–380px    │
│            │                              │              │
│ tabs       │  user bubble (blue, right)   │ entity name  │
│ search     │  AI answer blocks (full-w)   │ metrics      │
│ card grid  │  headings, tables, lists     │ kv rows      │
│            │  composer + hint (bottom)    │ chips/thumbs │
│            │                              │ status + CTA │
└────────────┴──────────────────────────────┴──────────────┘
```

- Whole thing may sit inside `.ac-page` (rounded, shadow-lg) as a full-screen
  overlay with a `.ac-pane-header` on top spanning all panes (title + status + close).
- The center pane scrolls; composer is sticky at bottom (`.ac-pane-footer`).
- The right pane is the *single source of truth* — it mirrors whatever the AI
  is configuring in chat, updating as the conversation progresses.

Skeleton:

```html
<body class="ac-app">
  <div class="ac-page" style="height:100vh">
    <header class="ac-pane-header"><!-- title + status + close --></header>
    <div class="ac-shell" style="height:auto;flex:1;min-height:0">
      <aside class="ac-pane" style="width:300px;flex:none"><!-- library --></aside>
      <main class="ac-pane is-canvas" style="flex:1">
        <div class="ac-pane-body"><!-- thread --></div>
        <div class="ac-pane-footer" style="border-top:0;background:transparent"><!-- composer --></div>
      </main>
      <aside class="ac-pane" style="width:360px;flex:none;border-left:1px solid var(--ac-border)"><!-- summary --></aside>
    </div>
  </div>
</body>
```

## B. Inbox workspace (4 columns) — e.g. lead CRM / IM console

```
┌──┬───────────────┬──────────────────────────┬─────────────┐
│R │ Filters+List  │  Thread                  │ Battle card │
│56│ 340–380px     │  flex, min 480px         │ 320–340px   │
│  │               │                          │             │
│  │ pill filters  │  thread header (name,    │ tags        │
│  │ dropdowns     │   phone, actions)        │ stepper     │
│  │ search        │  bubbles (gray canvas)   │ kv rows     │
│  │ items w/ tags │  banners above composer  │ action grid │
│  │               │  AI suggest + composer   │ timeline    │
└──┴───────────────┴──────────────────────────┴─────────────┘
```

- Rail `.ac-rail` is the app-level nav (dark). Only place dark chrome appears.
- List pane: `.ac-pane-header` holds filter pills + dropdown row + search
  (stacked, so header grows); body `.is-flush` with `.ac-list`.
- Thread pane `.is-canvas`; its own `.ac-pane-header` shows contact identity +
  right-aligned actions (WhatsApp link-out, 结束接管, close).
- Banners (`.ac-banner`) sit between thread body and composer, flush.
- Battle card pane has `border-left`, scrolls independently.

## C. Single-pane feed — e.g. dashboard/report page

Center column `max-width: 960px; margin: 0 auto; padding: 24px` on the gray canvas,
stacked `.ac-card`s: metric row card, table card, chart card. Page header row above
cards: `.ac-title` + `.ac-pill-row` of time-range filters + primary button right.
Use for analytics pages linked from `看数据 →`.

## D. Settings / form page

Two columns on canvas: sticky left mini-nav (200px, ghost buttons, active state
`background: var(--ac-primary-soft); color: var(--ac-primary)`), right stack of
`.ac-card`s each with `.ac-accent-heading` title, form rows
(label 12px `--ac-text-3` above `.ac-input`), card footer right-aligned buttons.

## Shared rules

- **Scrolling**: each pane scrolls its own `.ac-pane-body`; the shell never scrolls.
- **Borders between panes**, never gaps. Gaps (`--ac-gap`) exist only *inside* panes.
- **Responsive**: below 1200px hide the left library/list pane behind a toggle;
  below 900px the detail pane becomes a slide-over (`position:fixed; right:0`,
  `box-shadow: var(--ac-shadow-lg)`). The rail persists at all widths.
- **Empty states**: center an icon (24px, `--ac-text-3`) + one 13px gray line +
  optional outline button. No illustrations.
- **Overlay pages** (archetype A) darken the underlying app with `--ac-scrim`.
