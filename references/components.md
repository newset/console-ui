# Component Recipes — Agent Console UI

Every snippet works as-is with `assets/agent-console.css`. Root element needs class
`ac-app`. Icons: inline SVG, 15–19px, `stroke-width: 1.8–2`, `currentColor`
(Lucide/Feather style). Snippets below use a few inline icons; swap freely.

Table of contents:
1. [Shell: rail, pane header, footer links](#1-shell)
2. [Tags, pills, chips, status](#2-tags-pills-chips-status)
3. [Tabs & search](#3-tabs--search)
4. [Buttons](#4-buttons)
5. [Metrics & key-value rows](#5-metrics--key-value)
6. [Comparison table](#6-comparison-table)
7. [Chat: bubbles, meta, AI answer block](#7-chat)
8. [AI suggestion card](#8-ai-suggestion-card)
9. [Notice banners](#9-notice-banners)
10. [Composer](#10-composer)
11. [Conversation list item](#11-conversation-list-item)
12. [Pipeline stepper](#12-pipeline-stepper)
13. [Battle card (detail panel)](#13-battle-card)
14. [Campaign summary panel](#14-campaign-summary-panel)
15. [Asset / creative cards](#15-asset--creative-cards)
16. [Timeline](#16-timeline)
17. [Section heading & accent quote](#17-section-heading)

---

## 1. Shell

### Dark icon rail

```html
<nav class="ac-rail">
  <button class="ac-rail-btn is-active" title="对话">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
  </button>
  <button class="ac-rail-btn" title="数据">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M3 3v18h18"/><path d="M7 13v5M12 9v9M17 5v13"/></svg>
  </button>
  <div class="ac-rail-spacer"></div>
  <button class="ac-rail-btn" title="设置">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><circle cx="12" cy="12" r="3"/><path d="M12 1v4m0 14v4M4.2 4.2l2.8 2.8m10 10 2.8 2.8M1 12h4m14 0h4M4.2 19.8 7 17m10-10 2.8-2.8"/></svg>
  </button>
</nav>
```

### Pane header with status + close

The header line packs: title (may contain mono segments), then a second row of
status dot + muted tags. Close button floats right.

```html
<header class="ac-pane-header">
  <div style="flex:1;min-width:0">
    <div class="ac-title ac-ellipsis">吉利银河星耀6 · AZ/GE/KZ B2B经销商 CTW投放 · ABO · <span class="ac-num">$90/天</span> · 1个月</div>
    <div class="ac-row" style="margin-top:4px">
      <span class="ac-status is-paused"><span class="ac-dot is-paused"></span>已暂停</span>
      <span class="ac-tag is-blue">整车</span>
    </div>
  </div>
  <button class="ac-close"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 6 6 18M6 6l12 12"/></svg></button>
</header>
```

### Footer link row

```html
<div class="ac-links">
  <a href="#">看数据</a><a href="#">看询盘</a><a href="#">Meta 后台</a>
</div>
```

## 2. Tags, pills, chips, status

Semantic meaning is fixed — do not shuffle hues:

```html
<div class="ac-tag-row">
  <span class="ac-tag is-green">高质量</span>   <!-- quality grade / positive -->
  <span class="ac-tag is-red">人工跟进中</span>  <!-- needs human / urgent -->
  <span class="ac-tag is-blue">AI 跟进中</span>  <!-- AI-owned / info -->
  <span class="ac-tag is-gold">高价值</span>     <!-- premium / money -->
  <span class="ac-tag is-amber">待补充</span>    <!-- pending / caution -->
  <span class="ac-tag">基础</span>              <!-- neutral -->
  <span class="ac-tag is-outline">vehicle</span><!-- metadata / category -->
</div>
```

Filter pills (round, with mono counts; one `.is-active`):

```html
<div class="ac-pill-row">
  <button class="ac-pill is-active">全部 <span class="ac-pill-count">9587</span></button>
  <button class="ac-pill"><span class="ac-dot is-error"></span>人工跟进中 <span class="ac-pill-count">886</span></button>
  <button class="ac-pill"><span class="ac-dot is-info"></span>AI跟进中 <span class="ac-pill-count">8226</span></button>
  <button class="ac-pill"><span class="ac-dot"></span>AI 已结单 <span class="ac-pill-count">475</span></button>
</div>
```

Ad-group chips (mono label + count bubble):

```html
<div class="ac-row" style="flex-wrap:wrap">
  <span class="ac-chip ac-ellipsis">FB_AZ_IMPORTERS_MOBILE_AND <span class="ac-chip-count">2</span></span>
  <span class="ac-chip is-muted ac-ellipsis">FB_GE_REEXPORT_MOBILE</span>
</div>
```

## 3. Tabs & search

```html
<div class="ac-tabs">
  <button class="ac-tab is-active">Ogilvy创编 <span class="ac-tab-count">200</span></button>
  <button class="ac-tab">Medici知识库 <span class="ac-tab-count">62</span></button>
</div>

<div class="ac-search">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="7"/><path d="m21 21-4.3-4.3"/></svg>
  <input class="ac-input" placeholder="搜索素材">
</div>
```

## 4. Buttons

One `.is-primary` per pane, max. `✦` sparkle prefix is idiomatic for AI actions.

```html
<button class="ac-btn is-primary">✦ 恢复投放</button>
<button class="ac-btn is-outline">标记已报价</button>
<button class="ac-btn is-ghost">换一条 ↻</button>
<button class="ac-btn is-danger-soft" style="width:100%">标记丢单</button>
<button class="ac-btn is-outline is-icon" title="刷新"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12a9 9 0 1 1-2.64-6.36M21 3v6h-6"/></svg></button>
```

Action grid (battle-card operations — outline buttons, 2 columns):

```html
<div class="ac-btn-grid">
  <button class="ac-btn is-outline">标记已报价</button>
  <button class="ac-btn is-outline">已发送 PI/合同</button>
  <button class="ac-btn is-outline">已交订金</button>
  <button class="ac-btn is-outline">补录成单</button>
</div>
```

## 5. Metrics & key-value

Metric pair — label on top, big mono value, muted sub:

```html
<div class="ac-metric-row">
  <div>
    <div class="ac-metric-label">日预算</div>
    <div class="ac-metric-value">$90.00</div>
    <div class="ac-metric-sub">· <span class="ac-num">30</span> 天</div>
  </div>
  <div>
    <div class="ac-metric-label">预估对话</div>
    <div class="ac-metric-value">675-1800</div>
    <div class="ac-metric-sub">· 单价 <span class="ac-num">$1.5-$4</span></div>
  </div>
</div>
```

Key-value rows (labels gray 12px fixed-width; unknown values are `—` with `.is-empty`):

```html
<div class="ac-kv">
  <div class="ac-kv-row"><span class="ac-kv-label">客户国家</span><span class="ac-kv-value">United Arab Emirates</span></div>
  <div class="ac-kv-row"><span class="ac-kv-label">数量</span><span class="ac-kv-value ac-num">60 台</span></div>
  <div class="ac-kv-row"><span class="ac-kv-label">目的港</span><span class="ac-kv-value is-empty">—</span></div>
  <div class="ac-kv-row"><span class="ac-kv-label">Meta ID</span><span class="ac-kv-value ac-num">AE.1033692715675096</span></div>
</div>
```

Inline stat strip:

```html
<div class="ac-statline">
  <span>289.1K / 1.00M</span><span class="ac-sep">·</span>
  <span>29%</span><span class="ac-sep">·</span><span>$5.76</span>
</div>
```

## 6. Comparison table

First column = row labels (soft bg, dark text). Header row = primary-soft tint.
Use ✅/⚠️ sparingly for capability rows.

```html
<table class="ac-table">
  <thead><tr><th></th><th>B2B(经销商/进口商)</th><th>B2C(终端买家/个人车主)</th></tr></thead>
  <tbody>
    <tr><td>目标受众</td><td>当地汽车经销商、进口商、车队采购</td><td>普通消费者、个人购车者</td></tr>
    <tr><td>广告诉求</td><td>现货批量、FOB价格、出口单证</td><td>性能、颜值、驾驶体验</td></tr>
    <tr><td>系统支持</td><td>✅ V_1.0 完整支持</td><td>⚠️ 设计面向 B2B,B2C 效果有限</td></tr>
  </tbody>
</table>
```

## 7. Chat

Customer thread (bilingual outgoing bubble; meta outside the bubble):

```html
<div class="ac-thread">
  <div class="ac-msg is-in">
    <div class="ac-msg-meta"><span class="ac-msg-sender">Waleed Lashen, Trojan</span><span>16:51</span></div>
    <div class="ac-bubble">Trojan</div>
  </div>

  <div class="ac-msg is-out">
    <div class="ac-bubble">
      Perfect — 50Hz outdoor, UAE project. We have the full range covering 100/250/500 kVA.
      Could you share your company name?
      <div class="ac-bubble-sub">完美——50Hz户外,阿联酋项目。我们拥有涵盖100/250/500 kVA的全系列产品。能否请您分享一下贵公司的名称?</div>
    </div>
    <div class="ac-msg-meta"><span class="ac-msg-sender is-ai">AI Agent</span><span>16:51</span><span class="is-read">✓✓ 已读</span></div>
  </div>
</div>
```

Copilot chat (user bubble + full-width AI answer with rich content):

```html
<div class="ac-thread" style="gap:20px">
  <div class="ac-msg is-out">
    <div class="ac-bubble">做一个吉利星耀6的meta投放的广告。投放的国家是阿塞拜疆 + 格鲁吉亚 + 哈萨克斯坦。每个国家30刀的预算 投放1个月</div>
  </div>
  <div class="ac-answer">
    <p>好,信息收集得差不多了。现在我需要先了解几个关键点才能正式进入阶段 1。</p>
    <h3 class="ac-accent-heading is-lg">需求快速确认</h3>
    <p class="ac-t2">感谢你的信息,有几个问题要先确认一下:</p>
    <!-- tables, headings, lists ... -->
  </div>
</div>
```

## 8. AI suggestion card

```html
<div class="ac-suggest">
  <div class="ac-suggest-head">
    <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2l1.9 5.7a2 2 0 0 0 1.3 1.3L21 11l-5.8 1.9a2 2 0 0 0-1.3 1.3L12 20l-1.9-5.8a2 2 0 0 0-1.3-1.3L3 11l5.8-2a2 2 0 0 0 1.3-1.3L12 2z"/></svg>
    AI 建议回复
    <span class="ac-suggest-action">换一条 ↻</span>
  </div>
  <div class="ac-suggest-body">
    谢谢,Trojan!您的完整需求已记录——60+ 台机组(100/250/500 kVA),户外型,50Hz,阿联酋。我们销售团队将尽快与您联系。
    <div class="ac-t3" style="margin-top:6px">客户语言: Thanks, Trojan! Your full requirements are noted — our sales team will reach out shortly.</div>
  </div>
  <div class="ac-suggest-foot">
    <span class="ac-t3 ac-sm">依据: 通用话术</span>
    <button class="ac-btn is-primary is-sm">采纳建议 ↓</button>
  </div>
</div>
```

## 9. Notice banners

Stack directly above the composer, full width, no gaps:

```html
<div class="ac-banner is-warning">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M12 8v4M12 16h.01"/></svg>
  <span><b>人工接管中</b> 现在你的消息会发给客户,AI 已暂停。最长保留 <span class="ac-num">12</span> 小时。</span>
</div>
<div class="ac-banner is-success">
  <span class="ac-dot is-live"></span>
  <span><span class="ac-num">24</span> 小时窗口剩余 <span class="ac-num">22 小时 24 分</span> 窗口内可自由发消息</span>
  <span class="ac-banner-action">📋 模板消息</span>
</div>
```

## 10. Composer

```html
<div class="ac-composer">
  <textarea rows="1" placeholder="输入消息,可点「翻译」译成客户语言后再手改、发送"></textarea>
  <div class="ac-composer-bar">
    <button class="ac-btn is-ghost is-sm">📎 附件</button>
    <button class="ac-btn is-ghost is-sm">🎙 语音</button>
    <span class="ac-spring"></span>
    <button class="ac-btn is-outline is-sm">🌐 翻译</button>
    <button class="ac-btn is-primary is-sm">发送</button>
  </div>
</div>
```

Copilot variant swaps the hint line: `<div class="ac-composer-hint">Click-to-WhatsApp 投放 · 优化最大化 WhatsApp 对话数 · 上传图片 / PDF / Word / Markdown · 最大 50MB</div>`
and the send button becomes a round icon button.

## 11. Conversation list item

```html
<div class="ac-list">
  <div class="ac-list-item is-active">
    <div class="ac-avatar">WL</div>
    <div class="ac-list-main">
      <div class="ac-list-top">
        <span class="ac-list-name">Waleed Lashen, Trojan</span>
        <span class="ac-list-time">1 小时前</span>
      </div>
      <div class="ac-list-line ac-num">971565542260 <span class="ac-flag">🇦🇪</span> <span class="ac-t3" style="font-family:var(--ac-font)">United Arab Emirates</span></div>
      <div class="ac-tag-row">
        <span class="ac-tag is-green">中质量</span>
        <span class="ac-tag is-red">人工跟进中</span>
        <span class="ac-tag is-gold">高价值</span>
        <span class="ac-tag is-blue ac-num">1 条线索</span>
      </div>
      <div class="ac-list-snippet">客户来自阿联酋,公司名 Trojan,在建项目需采购60台以上干式变压器(500kVA×4台、250kVA×14台…</div>
    </div>
  </div>
</div>
```

## 12. Pipeline stepper

Segments: `.is-done` (green) → `.is-current` (blue) → default (gray). Labels mirror
the states. Idiomatic pipeline: 接待中 → 需求明确 → 已报价 → PI/合同 → 已交订金 → 成单/丢单.

```html
<div class="ac-stepper">
  <div class="ac-stepper-track">
    <div class="ac-step is-done"></div>
    <div class="ac-step is-current"></div>
    <div class="ac-step"></div>
    <div class="ac-step"></div>
    <div class="ac-step"></div>
    <div class="ac-step"></div>
  </div>
  <div class="ac-stepper-labels">
    <span class="is-done">接待中</span><span class="is-current">需求明确</span>
    <span>已报价</span><span>PI/合同</span><span>已交订金</span><span>成单/丢单</span>
  </div>
</div>
```

## 13. Battle card

The right-pane customer card. Order is fixed: label → name → tags → owner row →
stepper → kv rows → lead-detail link → actions → danger action → timeline.

```html
<aside class="ac-pane" style="width:340px">
  <div class="ac-pane-body">
    <div class="ac-stack">
      <div class="ac-row"><span class="ac-t3 ac-sm">客户作战卡</span><span class="ac-spring"></span><span class="ac-t3">☆</span></div>
      <div class="ac-title">Waleed Lashen, Trojan</div>
      <div class="ac-tag-row">
        <span class="ac-tag is-green">中质量</span><span class="ac-tag is-gold">高价值</span><span class="ac-tag is-blue">需求明确</span>
      </div>
      <div class="ac-card is-soft ac-row" style="padding:8px 12px">
        <span class="ac-sm">跟进负责人</span><span class="ac-spring"></span><span class="ac-strong ac-sm">当前账号</span>
      </div>
      <!-- stepper (recipe 12) -->
      <div class="ac-kv is-divided"><!-- kv rows (recipe 5) --></div>
      <a href="#" class="ac-sm">▸ 线索详情 · 全部字段(1条)</a>
      <div class="ac-t3 ac-sm">状态推进</div>
      <div class="ac-btn-grid"><!-- action grid (recipe 4) --></div>
      <button class="ac-btn is-danger-soft" style="width:100%">标记丢单</button>
      <div class="ac-t3 ac-sm">跟进记录</div>
      <div class="ac-timeline"><!-- recipe 16 --></div>
    </div>
  </div>
</aside>
```

## 14. Campaign summary panel

Right pane of the copilot console. Order: campaign name (mono) → metric pair →
contact card → chips → kv targeting rows → ad preview thumbs → status + actions → links.

```html
<aside class="ac-pane" style="width:360px">
  <div class="ac-pane-body">
    <div class="ac-stack">
      <div><span class="ac-t3 ac-sm">广告系列</span> <span class="ac-num ac-strong">Geely_Starshine6_CTW_B2B_AZ-GE-KZ</span></div>
      <!-- metric pair (recipe 5) -->
      <div class="ac-t3 ac-sm">询盘落地</div>
      <div class="ac-contact">
        <div class="ac-contact-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg></div>
        <div><div class="ac-num ac-strong">+86 185 8855 7892</div><div class="ac-t3 ac-sm">RevoPanda Auto Export</div></div>
      </div>
      <div class="ac-t3 ac-sm">广告组 · <span class="ac-num">3</span></div>
      <!-- chips (recipe 2), kv rows with 地区/年龄/兴趣/排期 -->
      <div class="ac-t3 ac-sm">广告 · <span class="ac-num">2</span> 点击预览</div>
      <div class="ac-row"><!-- .ac-thumb × n --></div>
      <div class="ac-row">
        <span class="ac-status is-paused"><span class="ac-dot is-paused"></span>已暂停</span>
        <span class="ac-spring"></span>
        <button class="ac-btn is-outline is-icon">↻</button>
        <button class="ac-btn is-primary">✦ 恢复投放</button>
      </div>
      <hr class="ac-divider">
      <div class="ac-links"><a href="#">看数据</a><a href="#">看询盘</a><a href="#">Meta 后台</a></div>
    </div>
  </div>
</aside>
```

Note the "interest" values in targeting kv rows render as a wrap of outline tags:

```html
<div class="ac-kv-row"><span class="ac-kv-label">兴趣</span>
  <span class="ac-kv-value"><span class="ac-tag-row">
    <span class="ac-tag is-outline">car dealer</span>
    <span class="ac-tag is-outline">automotive importer</span>
    <span class="ac-tag is-outline">international trade</span>
  </span></span>
</div>
```

## 15. Asset / creative cards

2-column grid; portrait 4:5 media; `AI` corner badge + caption on top; WhatsApp CTA
chip bottom-right. In demos use `.ac-ph` gradient placeholders instead of images.

```html
<div class="ac-asset-grid">
  <figure class="ac-asset" style="margin:0">
    <div class="ac-asset-media"><span class="ac-ph is-dusk"></span></div>
    <span class="ac-asset-badge">AI</span>
    <figcaption class="ac-asset-caption">Быстрая отгрузка · Geely Galaxy A7</figcaption>
    <span class="ac-asset-cta">🟢 WhatsApp</span>
  </figure>
</div>
```

## 16. Timeline

```html
<div class="ac-timeline">
  <div class="ac-timeline-item">
    <div class="ac-timeline-dot"></div>
    <div class="ac-timeline-body">
      <div class="ac-timeline-time">今天 16:51</div>
      转人工跟进,客户要求正式报价。
    </div>
  </div>
</div>
```

## 17. Section heading

Inside AI answers and panel sections:

```html
<h3 class="ac-accent-heading is-lg">需求快速确认</h3>
<h4 class="ac-accent-heading">1. 业务模式是 B2B 还是 B2C?</h4>
```

Emphasis callout inside answer text — same accent bar on a body line:

```html
<p class="ac-accent-heading" style="font-weight:400;font-size:13px">
  <span><b>这个很关键</b>,因为两种模式的受众、文案、创意策略完全不同:</span>
</p>
```
