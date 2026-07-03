<sub>🌐 <a href="README.md">中文</a> · <b>English</b></sub>

<div align="center">

# Agent Console UI

> *"One sentence in, a production-grade ops console out."*

[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Agent-Agnostic](https://img.shields.io/badge/Agent-Agnostic-blueviolet)](https://skills.sh)
[![Style](https://img.shields.io/badge/Style-AI%20Agent%20Console-2E6BE6)](references/design-tokens.md)

<br>

**A design-system skill that teaches your agent the "AI Agent Operations Console" aesthetic.**

<br>

Not "decent for AI" pages — the information-dense, chat-centric operator workspaces you see in modern Chinese B2B SaaS: AI campaign copilots, WhatsApp lead CRMs, AI customer-service consoles. Calm light-gray canvas, white rounded panels, one saturated blue, semantic pastel tags, monospace numerals, bilingual chat bubbles.

```
npx skills add <your-github-username>/agent-console-ui
```

Works across agents — Claude Code, Cursor, Codex, and anything that supports skills.

</div>

---

## Install & use

```bash
npx skills add <your-github-username>/agent-console-ui
```

Or copy this repo into your skills directory (`.claude/skills/agent-console-ui/` for a project, `~/.claude/skills/agent-console-ui/` for personal). Then just ask:

```
"Build an AI campaign console: asset library left, chat center, campaign summary right"
"Make a WhatsApp lead CRM inbox with a customer battle card and pipeline stages"
"A dark, compact customer-support operations workspace"
"A green-accent trade-inquiry management console"
```

## What it does

| Capability | Details |
|---|---|
| 3-pane copilot console | Asset library + AI chat (accent-bar headings, comparison tables) + live summary pane |
| Inbox workspace | Dark icon rail + filtered list + bilingual thread + customer battle card |
| Dashboard / settings pages | Single-column feed and two-column form archetypes |
| Full component library | 17 recipes: semantic tags, filter pills, bilingual bubbles, AI suggestion card, stepper, timeline, comparison table… |
| One-attribute variants | `data-ac-theme="dark"` · `data-ac-accent="green/violet/orange"` · `data-ac-density="compact"`, freely combined |
| Design tokens | Every color/size/radius is a CSS variable — retheme without touching component CSS |

## See the style

Two faithful reference implementations (open locally after cloning):

```bash
python3 -m http.server 8080
# http://localhost:8080/examples/campaign-console.html   ← AI campaign copilot (3 panes)
# http://localhost:8080/examples/lead-inbox.html         ← WhatsApp lead CRM (4 columns)
```

The first four of the ten iron rules:

1. Canvas `#F4F6F9`, pure-white panels with 1px borders, near-invisible shadows;
2. Exactly one loud color, `#2E6BE6` (bubbles, primary buttons, active states, heading bars);
3. All numerals in monospace (`$90.00`, `675-1800`, phones, IDs);
4. Tags are small, squarish, pastel, semantically fixed: green=quality, red=human, blue=AI, gold=high-value.

Full rules in [SKILL.md](SKILL.md); exact values in [references/design-tokens.md](references/design-tokens.md).

## Repository layout

```
agent-console-ui/
├── SKILL.md                  # agent instructions: routing table + ten iron rules + taboo list
├── assets/agent-console.css  # drop-in stylesheet: tokens + all ac- components + variants
├── references/               # design-tokens / components / layouts / variants
├── examples/                 # campaign-console.html · lead-inbox.html
└── test-prompts.json         # trigger & quality test prompts
```

## License

MIT — free for personal and commercial use.
