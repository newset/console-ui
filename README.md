<sub>🌐 <b>中文</b> · <a href="README.en.md">English</a></sub>

<div align="center">

# Agent Console UI

> *「一句话,拿回一个像大厂 B 端团队做的工作台。」*
> *"One sentence in, a production-grade ops console out."*

[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Agent-Agnostic](https://img.shields.io/badge/Agent-Agnostic-blueviolet)](https://skills.sh)
[![Style](https://img.shields.io/badge/Style-AI%20Agent%20Console-2E6BE6)](references/design-tokens.md)

<br>

**给你的 agent 装一套「AI 智能体运营工作台」设计体系。**

<br>

它生成的不是"AI 做的还行"的页面——是现代中文 B2B SaaS 里那种信息密度高、以对话为中心的操作台:AI 投放副驾、WhatsApp 线索 CRM、AI 客服控制台。浅灰画布、白色圆角面板、全页唯一的高饱和蓝、语义化彩色标签、等宽数字、中英双语气泡。

```
npx skills add <your-github-username>/agent-console-ui
```

跨 agent 通用——Claude Code、Cursor、Codex 等支持 skills 的 agent 都能装。

[能做什么](#能做什么) · [装上就能用](#装上就能用) · [风格长什么样](#风格长什么样) · [变体](#变体) · [仓库结构](#仓库结构)

</div>

---

## 装上就能用

```bash
npx skills add <your-github-username>/agent-console-ui
```

或手动安装:把本仓库拷到 skills 目录

- Claude Code(项目级): `.claude/skills/agent-console-ui/`
- Claude Code(个人级): `~/.claude/skills/agent-console-ui/`

然后直接说话:

```
「做一个 AI 投放控制台,左边素材库、中间对话、右边广告系列摘要」
「做个 WhatsApp 线索 CRM 收件箱,带客户作战卡和跟进阶段」
「深色紧凑的客服运营工作台」
「绿色主题的外贸询盘管理台」
```

## 能做什么

| 能力 | 说明 |
|------|------|
| 三栏 Copilot 控制台 | 素材库 + AI 对话(带蓝竖条标题、对比表)+ 实时摘要面板 |
| 收件箱工作台 | 深色图标侧栏 + 筛选列表 + 双语聊天线程 + 客户作战卡 |
| 数据看板 / 设置页 | 单栏 feed 与双栏表单两种原型 |
| 完整组件库 | 17 组配方:语义标签、筛选 pill、双语气泡、AI 建议卡、stepper、时间线、对比表… |
| 一键变体 | `data-ac-theme="dark"` · `data-ac-accent="green/violet/orange"` · `data-ac-density="compact"`,任意组合 |
| 设计令牌 | 全部颜色/字号/间距/圆角是 CSS 变量,换主题不改一行组件代码 |

## 风格长什么样

两个忠实还原的参考实现(克隆后本地打开):

```bash
python3 -m http.server 8080
# http://localhost:8080/examples/campaign-console.html  ← AI 投放副驾(三栏)
# http://localhost:8080/examples/lead-inbox.html        ← WhatsApp 线索 CRM(四栏)
```

风格核心,十条铁律的前四条:

1. 画布 `#F4F6F9`,面板纯白 + 1px 描边,阴影几乎不可见;
2. 全页只有一个响亮的蓝 `#2E6BE6`(气泡、主按钮、激活态、标题竖条);
3. 所有数字等宽字体(`$90.00`、`675-1800`、电话、ID);
4. 标签小方粉彩、语义固定:绿=质量、红=人工、蓝=AI、金=高价值。

完整规则见 [SKILL.md](SKILL.md),精确数值见 [references/design-tokens.md](references/design-tokens.md)。

## 变体

在 `<html>` 上加 data 属性,可任意组合,零 CSS 改动:

| 属性 | 取值 | 场景 |
|---|---|---|
| `data-ac-theme` | `dark` | 夜间运营台 |
| `data-ac-accent` | `green` / `violet` / `orange` | 外贸·WhatsApp / 分析·AI / 电商 |
| `data-ac-density` | `compact` | 高密度操作员模式 |

## 仓库结构

```
agent-console-ui/
├── SKILL.md                  # agent 指令:任务路由表 + 十条铁律 + 禁忌清单
├── assets/
│   └── agent-console.css     # 即插即用样式表:令牌 + 全部 ac- 组件 + 变体
├── references/
│   ├── design-tokens.md      # 颜色/字体/间距/圆角/阴影 + 暗色映射
│   ├── components.md         # 17 组可复制组件配方
│   ├── layouts.md            # 4 种布局原型
│   └── variants.md           # 变体系统 + 新主题色扩展规则
├── examples/
│   ├── campaign-console.html # 参考实现 A:AI 投放控制台
│   └── lead-inbox.html       # 参考实现 B:线索收件箱
└── test-prompts.json         # 触发与质量测试提示词
```

## License

MIT——个人和商用都免费。