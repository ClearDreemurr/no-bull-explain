<div align="center">

[![English](https://img.shields.io/badge/English-blue?style=flat-square)](README.md)
[![中文](https://img.shields.io/badge/中文-red?style=flat-square)](README.zh.md)

</div>

<br>

<div align="center">

# no-bull-explain

一款给 AI 编程助手（Claude Code、OpenAI Codex Copilot）用的教学技能，帮你低认知负担地解释复杂概念。

[![Claude Code compatible](https://img.shields.io/badge/Claude%20Code-compatible-8A2BE2)](https://claude.ai/code)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

## 它做什么

不是复述术语，而是帮用户亲手长出一个准确的理解模型：

1. **先卸载术语** — 从无变量、无黑话的低配场景开始
2. **找到最小可运行模型** — 只保留让概念成立的最小机制
3. **重现发明者的痛点** — 先看到朴素做法怎么坏，再引出真实方案
4. **先局部再全局** — 让一个格子、一个状态先动起来，再推广
5. **映射回真实术语** — 直觉搭好后再给技术名字
6. **去魔法化收尾** — 落到数据、状态、规则、参数、流程等底层对象

## 什么时候用

当有人让你**解释、教学、简化、澄清或重写**一个困难概念时：

- 用户说"我不懂 X"或"把我当小白讲"
- 某个技术概念一次抛了太多新术语
- 用户已经试过其他解释但还没搞懂
- 你在写文档、教程或教学示例

## 安装

### Claude Code

```bash
npx skills add ClearDreemurr/no-bull-explain
```

或者手动：

```bash
mkdir -p ~/.claude/skills/no-bull-explain
cp SKILL.md ~/.claude/skills/no-bull-explain/
```

> 英文版请复制 `SKILL.en.md`。

### OpenAI Codex Copilot

通过 `~/.codes/skills/` 配合 `agents/openai.yaml` 配置安装。

## 用法

安装后在 Claude Code 中直接调用：

```
/no-bull-explain
```

或者让 AI 自动判断你的请求是否匹配该技能。

### 效果对比

| 不用 skill | 用 skill 后 |
|---|---|
| "滑动窗口是 TCP 头部中使用窗口大小字段的流量控制机制..." | 从课上传纸条开始 → 为什么会顾不过来 → 滑动框如何解决 → 最后映射到 TCP 术语 |

完整推演见 [examples/sliding-window.md](examples/sliding-window.md)。

### 效果展示

[examples/](examples/) 目录下有多篇由本 skill 实际生成的完整教学对话，可以直接看到效果：

| 示例 | 主题 |
|---|---|
| [N₂O₄ 化学平衡](examples/n2o4-chemical-equilibrium.md) | 勒夏特列原理——为什么压缩容器会让平衡移动 |
| [CPU 缓存与局部性原理](examples/缓存与局部性原理详解.md) | 为什么缓存不是越大越好，改一行代码怎么快 200 倍 |

## 它怎么工作

技能分两个层次：

**核心流程** — 一套跨任何技术领域的 9 步教学流：

1. 卸载所有术语
2. 搭低配场景
3. 展示朴素做法怎么坏
4. 追踪一个局部动作
5. 停下来确认
6. 映射回真实术语
7. 用自然语言描述公式逻辑
8. 说明简化边界
9. 给出去魔法化定义

**文字化动态推演** — 对于涉及过程、空间关系或状态变化的概念（如卷积、注意力机制、DP 表、网络协议），技能用逐帧文字推理让看不见的变化变得可追踪。

## 文件结构

```
no-bull-explain/
├── SKILL.md              ← 技能定义（中文）
├── SKILL.en.md           ← 技能定义（英文）
├── README.md             ← 本文件（英文）
├── README.zh.md          ← README（中文）
├── LICENSE               ← MIT 许可证
├── agents/
│   └── openai.yaml       ← OpenAI Codex Copilot 集成配置
└── examples/
    ├── sliding-window.md            ← TCP 滑动窗口（few-shot 模板）
    ├── n2o4-chemical-equilibrium.md ← 化学平衡 · 勒夏特列原理
    └── 缓存与局部性原理详解.md       ← CPU 缓存与局部性原理
```

## 许可证

MIT — 见 [LICENSE](LICENSE)。
