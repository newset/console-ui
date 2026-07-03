# Variants — Agent Console UI

All variants are token swaps driven by `data-*` attributes. Never fork component CSS
or hand-pick new hex values for a variant — set the attribute and let tokens cascade.
Attributes go on `<html>`, `<body>`, or any container (they cascade from there).

## 1. Dark theme

```html
<html data-ac-theme="dark">
```

What changes: canvas `#12151C`, panels `#1A1E27`, borders lifted, text inverted to
`#E8EBF1`, primary lifted to `#4C82F0` for contrast, soft hues become deep tints.
What stays: outgoing bubbles stay primary-filled; tag semantics; layout; the rail
(just gets darker `#0D1016`).

Checklist when rendering dark:
- Incoming bubbles switch to `--ac-panel-soft` (the stylesheet does this).
- Image thumbs/placeholders keep their own colors — do not filter/dim media.
- Never use pure white text on colored soft backgrounds; tokens already handle it.

## 2. Accent themes

```html
<html data-ac-accent="green">   <!-- trade / WhatsApp-centric ops -->
<html data-ac-accent="violet">  <!-- analytics / AI-heavy tooling -->
<html data-ac-accent="orange">  <!-- e-commerce / marketplace ops -->
```

Only the primary family moves (bubbles, primary buttons, links, active states,
accent bars, blue tags become accent-colored). Semantic hues (success/warning/
danger/gold) are pinned so state meaning survives any accent.

Pick by product domain, not preference: blue = default console; green when WhatsApp
or trading is the heart of the product; violet for data/AI analysis tools; orange
for commerce. Combine freely with dark: `data-ac-theme="dark" data-ac-accent="violet"`.

## 3. Compact density

```html
<html data-ac-density="compact">
```

Shrinks paddings, gaps and row heights (~20%). Use for data-heavy operator screens
(inbox lists, tables) when the user asks for "更紧凑" / "dense" / "operator mode".
Font sizes do not change — only whitespace. Don't combine compact with marketing
or landing-style pages.

## 4. Sub-brand recipes (combinations that work)

| Ask | Attributes |
|---|---|
| "夜间模式的客服工作台" | `data-ac-theme="dark"` |
| "绿色主题的外贸询盘 CRM" | `data-ac-accent="green"` |
| "紧凑的深色运营看板" | `data-ac-theme="dark" data-ac-density="compact"` |
| "AI 分析工具,紫色调" | `data-ac-accent="violet"` |
| "电商订单工作台" | `data-ac-accent="orange" data-ac-density="compact"` |

## 5. Extending with a new accent

Add one block following the existing pattern — four tokens light + four dark:

```css
[data-ac-accent="teal"] {
  --ac-primary: #0E9BA6; --ac-primary-strong: #0B7B84;
  --ac-primary-soft: #E3F4F6; --ac-primary-border: #B0DEE2;
}
[data-ac-theme="dark"][data-ac-accent="teal"] {
  --ac-primary: #2FB8C4; --ac-primary-strong: #55C9D3;
  --ac-primary-soft: #14313A; --ac-primary-border: #1E4750;
}
```

Rules for choosing values: `primary` ≈ L 45–55 in light / lifted ~10 in dark;
`soft` is a ~92% tint of primary on white (light) or ~80% shade on panel (dark);
`border` sits halfway between soft and primary. Keep contrast of white text on
`primary` ≥ 4.5:1.

## 6. Theme switcher snippet

```html
<script>
  const root = document.documentElement;
  function setTheme(t)   { t ? root.dataset.acTheme = t : delete root.dataset.acTheme; }
  function setAccent(a)  { a ? root.dataset.acAccent = a : delete root.dataset.acAccent; }
  function setDensity(d) { d ? root.dataset.acDensity = d : delete root.dataset.acDensity; }
</script>
```
