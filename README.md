<div align="center">

[![English](https://img.shields.io/badge/English-blue?style=flat-square)](README.md)
[![中文](https://img.shields.io/badge/中文-red?style=flat-square)](README.zh.md)

</div>

<br>

<div align="center">

# explain-complex-concepts

A teaching skill for AI coding agents that explains complex concepts with low cognitive load.

[![Claude Code compatible](https://img.shields.io/badge/Claude%20Code-compatible-8A2BE2)](https://claude.ai/code)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

## What It Does

Instead of reciting jargon and formal definitions, this skill helps the AI build the user's understanding from the ground up:

1. **Unload jargon first** — start with a no-variable, no-terminology low-level scene
2. **Find the minimal working model** — only keep the smallest mechanism that makes the concept work
3. **Recreate the inventor's pain** — show why naive approaches fail before introducing the real solution
4. **Reason locally before generalizing** — make one cell, one state, or one object move first, then scale up
5. **Map back to real terms** — give technical names only after the intuition is built
6. **Close with a demystified definition** — ground everything in data, state, rules, parameters, flow, or mapping

## When to Use

Use this skill whenever someone asks you to **explain, teach, simplify, clarify, or rewrite** a difficult idea — especially when:

- The user says "I don't understand X" or "explain X like I'm 5"
- A technical concept has too many new terms at once
- The user has tried other explanations but still doesn't get it
- You're writing documentation, a tutorial, or a teaching example

## Installation

### Claude Code

```bash
npx skills add ClearDreemurr/explain-complex-concepts
```

Or manually:

```bash
mkdir -p ~/.claude/skills/explain-complex-concepts
cp SKILL.md ~/.claude/skills/explain-complex-concepts/
```

> For the English version, use `SKILL.en.md` instead.

### OpenAI Codex Copilot

Install via `~/.codes/skills/` using the `agents/openai.yaml` config.

## Usage

Once installed, simply invoke the skill in Claude Code:

```
/explain-complex-concepts
```

Or let the AI auto-detect when your request fits the skill's purpose.

### Example

| Before (without skill) | After (with skill) |
|---|---|
| "Sliding window is a flow control mechanism using a window size field in TCP headers..." | Builds from passing notes in class → why you'd get overwhelmed → how a sliding frame solves it → then maps to TCP terminology |

See [examples/sliding-window.md](examples/sliding-window.md) for the full walkthrough.

### See It in Action

Browse the [examples/](examples/) directory to see full teaching conversations produced by this skill:

| Example | Topic |
|---|---|
| [N₂O₄ Chemical Equilibrium](examples/n2o4-chemical-equilibrium.md) | Le Chatelier's principle — why compressing a gas shifts the balance |
| [CPU Cache & Locality](examples/缓存与局部性原理详解.md) | Why bigger isn't faster, how cache hierarchy works, and how one line change makes code 200× faster |

## How It Works

The skill operates on two levels:

**Core principles** — a 9-step teaching flow that works across any technical domain:

1. Drop all terms
2. Set up a low-config scene
3. Show naive approach failing
4. Watch one local unit move
5. Pause and confirm
6. Map to real terminology
7. Describe formulas in plain language first
8. Explain where the model breaks down
9. Give a demystified definition

**Dynamic text visualization** — for concepts involving processes, spatial relationships, or state changes (e.g., convolution, attention mechanisms, DP tables, network protocols), the skill uses frame-by-frame text reasoning to make invisible changes trackable.

## Files

```
explain-complex-concepts/
├── SKILL.md              ← Skill definition (Chinese)\
├── SKILL.en.md           ← Skill definition (English)
├── README.md             ← This file (English)
├── README.zh.md          ← README (Chinese)
├── LICENSE               ← MIT License
├── agents/
│   └── openai.yaml       ← OpenAI Codex Copilot integration
└── examples/
    ├── sliding-window.md            ← TCP sliding window (few-shot template)
    ├── n2o4-chemical-equilibrium.md ← Le Chatelier's principle walkthrough
    └── 缓存与局部性原理详解.md       ← CPU cache & locality walkthrough
```

## License

MIT — see [LICENSE](LICENSE).
