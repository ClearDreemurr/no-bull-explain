# explain-complex-concepts / 清晰解释复杂概念

[![Claude Code compatible](https://img.shields.io/badge/Claude%20Code-compatible-8A2BE2)](https://claude.ai/code)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> A bilingual (中文 / English) teaching skill for AI coding agents.  
> Explains complex concepts with low cognitive load — unloads jargon first, builds intuition from minimal models, uses step-by-step dynamic reasoning before formulas.

---

## 🇨🇳 中文

### 这是什么

一个帮助 AI 编程助手（Claude Code、OpenAI Codex CLI）用**低认知负担**方式解释复杂概念的 skill。

核心流程：

1. **先卸载术语** — 不带变量、不带黑话，从低配场景开始
2. **找到最小可运行模型** — 只保留让概念成立的最小机制
3. **复现发明者痛点** — 先展示朴素做法的具体麻烦，再引出真实方案
4. **先讲局部动作** — 一个格子、一个状态、一个对象先动起来
5. **映射回真实术语** — 技术名称在理解建立后才给出
6. **去魔法化定义** — 落到数据、状态、规则、流程等底层对象

### 适用场景

当有人问你「解释一下 X」「我不懂 Y」「讲清楚 Z」时使用。特别适合：

- 算法（动态规划、滑动窗口、注意力机制）
- 网络协议（TCP、HTTP、DNS）
- 系统设计概念（缓存、负载均衡、分布式共识）
- 数学／统计概念（梯度下降、贝叶斯、信息熵）
- 编程范式（递归、闭包、异步、协程）

### 安装

```bash
# Claude Code
npx skills add ClearDreemurr/explain-complex-concepts
```

手动安装：

```bash
mkdir -p ~/.claude/skills/explain-complex-concepts
cp SKILL.md ~/.claude/skills/explain-complex-concepts/
```

> 如需英文版，将 `SKILL.md` 替换为 `SKILL.en.md`。

### 使用方法

安装后在 Claude Code 中调用：

```
/explain-complex-concepts
```

或直接问一个问题，AI 会自动匹配此 skill。

### 文件说明

```
explain-complex-concepts/
├── SKILL.md                  ← 中文版（原始版本）
├── SKILL.en.md               ← English version
├── README.md                 ← 中英双语说明（本文件）
├── LICENSE                   ← MIT 许可证
├── agents/
│   └── openai.yaml           ← OpenAI Codex CLI 配置
└── examples/
    └── sliding-window.md     ← 示例：TCP 滑动窗口推演
```

### 许可证

MIT — 详见 [LICENSE](LICENSE)。

---

## 🇬🇧 English

### What It Is

A teaching skill for AI coding agents (Claude Code, OpenAI Codex CLI) that explains complex concepts with **low cognitive load**.

Core workflow:

1. **Unload jargon first** — start with a no-variable, no-terminology low-level scene
2. **Find the minimal working model** — keep only the smallest mechanism that makes the concept work
3. **Recreate the inventor's pain** — show why naive approaches fail before introducing the real solution
4. **Local action first, then generalize** — make one cell, one state, or one object move first
5. **Map back to real terms** — technical names come only after the intuition is built
6. **Demystified definition** — ground everything in data, state, rules, flow, or mapping

### When to Use

Whenever someone asks you to **explain, teach, simplify, clarify** a difficult idea. Especially good for:

- Algorithms (dynamic programming, sliding window, attention mechanisms)
- Network protocols (TCP, HTTP, DNS)
- System design (caching, load balancing, distributed consensus)
- Math/statistics (gradient descent, Bayes, information entropy)
- Programming paradigms (recursion, closures, async, coroutines)

### Installation

```bash
# Claude Code
npx skills add ClearDreemurr/explain-complex-concepts
```

Manual install:

```bash
mkdir -p ~/.claude/skills/explain-complex-concepts
cp SKILL.en.md ~/.claude/skills/explain-complex-concepts/SKILL.md
```

### Usage

After installation, invoke in Claude Code:

```
/explain-complex-concepts
```

Or just ask a question — the AI will auto-match this skill.

### File Structure

```
explain-complex-concepts/
├── SKILL.md                  ← Chinese (original)
├── SKILL.en.md               ← English version
├── README.md                 ← Bilingual docs (this file)
├── LICENSE                   ← MIT License
├── agents/
│   └── openai.yaml           ← OpenAI Codex CLI config
└── examples/
    └── sliding-window.md     ← Example: TCP sliding window walkthrough
```

### License

MIT — see [LICENSE](LICENSE).
