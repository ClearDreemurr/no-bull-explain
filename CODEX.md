# explain-complex-concepts skill 接手文档

## 1. 当前目标

用户正在把一个优秀知识区博主“飞天闪客”的复杂概念讲解方法蒸馏成一个 Codex skill，目标不是角色扮演或模仿口癖，而是让 Codex 学会：

- 把复杂抽象概念拆成最小可运行模型
- 先讲逻辑和约束，再引入术语
- 使用结构同构的比喻、逐步推演、信息重组或公式拆解
- 用文字复现动态可视化的理解效果
- 最后给出准确、好记的极简定义

后续工作应继续围绕“证据 -> 机制 -> skill 修改”展开。不要让 NotebookLM 直接写 skill 内容；NotebookLM 只负责从视频文案里做材料分析报告，Codex 负责把关、提炼和修改 skill。

## 2. 本轮本地上下文

- 工作区：`D:\学习资料`
- 当前没有 `D:\学习资料\CODEX.md`，之前读取时不存在。
- Skill 安装目录：`C:\Users\zhanbohan\.codex\skills`
- 该目录在 workspace 外，读写通常需要授权。
- 敏感文件：`D:\学习资料\cookies.txt` 是 YouTube 登录 cookie，后续不要读取或暴露内容。

## 3. 已创建的 skill

已创建并验证通过：

- `C:\Users\zhanbohan\.codex\skills\explain-complex-concepts\SKILL.md`
- `C:\Users\zhanbohan\.codex\skills\explain-complex-concepts\agents\openai.yaml`

skill 名称：`explain-complex-concepts`

`quick_validate.py` 已通过，最后输出为：`Skill is valid!`

注意：写 `SKILL.md` 时曾遇到 PowerShell UTF-8 BOM 导致 frontmatter 校验失败，已用 .NET 写入 UTF-8 无 BOM 解决。后续改这个文件时，建议继续用：

```powershell
[System.IO.File]::WriteAllText($path, $content, [System.Text.UTF8Encoding]::new($false))
```

## 4. 当前 SKILL.md 核心内容

skill 正文是中文，frontmatter 是英文。核心结构包括：

- 核心流程
- 规则
- 路径选择
- 文字化动态推演
- 禁忌
- 最小回答结构
- 自检清单

新增的“文字化动态推演”章节已插入到 `路径选择` 后、`禁忌` 前。当前章节起始行大约在：

- `C:\Users\zhanbohan\.codex\skills\explain-complex-concepts\SKILL.md:55`

新增章节的核心规则：

- 动作化降解：把抽象关系改写成动作链
- 局部焦点：先追踪一个格子、一个 token、一个窗口、一个状态或一个数据包
- 空间外部化：用行、列、格子、槽位、窗口、箭头、表格把空间关系放到纸面上
- 时间分帧：用第 1 步 / 第 2 步 / 第 3 步展示状态变化
- 输入输出闭环：明确输出如何成为下一步输入
- 需求驱动术语：先展示朴素做法的麻烦，再引出术语

## 5. skill 验证结果

用户用 `explain/` 目录下 6 个讲解文档验证 skill。

目录：`D:\学习资料\explain`

文件包括：

- `bayesian-update-explained.md`
- `database-index-explained.md`
- `dp-explained.md`
- `oauth-explained.md`
- `tcp-congestion-control-explained.md`
- `transformer-attention-explained.md`

评分标准：7 项，每项 0-2，总分 14：

- 最小模型
- 核心矛盾/约束
- 路径选择
- 技术映射
- 边界说明
- 极简定义
- 术语控制/整体结构（实际评分时有时合并表达）

最终整体评分：

| 文档 | 分数 | 主要评价 |
|---|---:|---|
| `oauth-explained.md` | 13/14 | 最稳定，酒店访客卡比喻、映射、边界都很好。|
| `bayesian-update-explained.md` | 13/14 | 高中生友好，证据强度和信念更新讲清楚。小风险：`更新后的信任 = 原信任 × 证据权重`容易被误解为概率直接相乘，更严格说类似 odds 更新。|
| `database-index-explained.md` | 12/14 | 目录/字典比喻好，B+ 树解释完整。文本里有一句断裂：`不需要满字典找，集中的"`，需要清理。|
| `tcp-congestion-control-explained.md` | 12/14 | AIMD 讲得强，但“唯一已知的分布式收敛算法”说太满。|
| `dp-explained.md` | 12/14 | 本质讲清楚。盖楼比喻只解释顺序依赖，不够解释重复子问题复用；背包表格有自我纠错残留。|
| `transformer-attention-explained.md` | 11/14 | 小白友好，但 RNN“读完忘了开头”略粗糙；QKV 从向量变出来的过程讲得不够。|

结论：skill 初步有效。主要问题不是框架失效，而是局部质量控制：比喻同构性、技术表述过满、生成残留清理。

## 6. NotebookLM 分工和关键提醒

用户强调：NotebookLM 能看到的是视频文案/字幕，不是原视频画面。不要让它假装看到了动态画面。

正确分工：

- NotebookLM：基于全部视频文案做材料分析报告，找文案证据、模式、认知机制、风险。
- Codex：判断哪些有证据、哪些是脑补；把可靠机制提炼成 skill 修改方案；经用户确认后落文件。

不要再让 NotebookLM 输出“AI skill 修改内容”或 “SKILL.md 草案”。用户已经纠正过这一点。

推荐给 NotebookLM 的提问风格：

```text
请不要给 AI skill 修改建议，也不要写 SKILL.md 内容。你只需要基于视频文案做研究报告。
主题：飞天闪客如何通过“文字可视化/动态推演”让复杂概念变得易懂。
...
```

## 7. 已从 NotebookLM 获得的重要研究结论

NotebookLM 最近输出了一份“文字可视化与动态推演”研究报告，来源文件是：

- `D:\学习资料\lm.txt`

报告中可信度较高的发现：

- “动作化降解”：把抽象数学/结构关系改写成动作链，例如错位、放到这里、移动、传递、转动。
- “把公式变成动作”：把等式关系变成可追踪的对象运动。
- “降低工作记忆负担”：不用同时记多个变量名和下标，改为追踪物理对象属性。
- “降低空间想象负担”：高维张量用分层套娃、盒子/文件夹等层级结构处理。
- “降低时间顺序追踪负担”：RNN/Transformer/递归类概念强调输出如何接回输入、信息如何往下传。
- “从局部运算推广到整体结构”：先讲一个格子、一个 token、一个窗口，再推广到整体矩阵、序列、协议。
- “需求驱动逻辑，逻辑定义术语”：先让用户看到朴素做法哪里麻烦，术语成为解决问题后的自然出口。

需要降温或避免直接写入 skill 的部分：

- “强制剥离用户先验术语偏见”语气太强，应写成“先暂时搁置术语”。
- “碰撞、抓取、眼睛、目光”等表达只可作为偶尔技巧，不宜进入核心规则，否则拟人化太重。
- “社会博弈角色化”属于生活比喻，不是动态可视化主题，先不放进文字化动态推演章节。
- NotebookLM 提到视频画面时必须注意：它其实只基于文案推断，不能当作画面事实。

## 8. 之前关于视频风格的全样本分析

用户用 NotebookLM 对 45 个视频做了结构化分析。统计结果：

字段出现频率（N=45）：

| 字段 | 是/有 | 部分/不明确 | 否/无 |
|---|---:|---:|---:|
| 心理按摩/去魅 | 34 | 4 | 7 |
| 反直觉问题 | 41 | 0 | 4 |
| 生活比喻 | 36 | 0 | 9 |
| 视觉化推演 | 28 | 0 | 17 |
| 技术映射 | 44 | 0 | 1 |
| 一句话重新定义 | 43 | 2 | 0 |

清晰感来源频率：

| 标签 | 次数 |
|---|---:|
| 结构拆解 | 26 |
| 生活比喻 | 16 |
| 可视化/视觉化 | 14 |
| 信息重组/分类 | 9 |
| 立场去魅/去圣化 | 8 |
| 语言节奏/口语化 | 4 |
| 逻辑推导/博弈分析 | 3 |

稳定机制：

- 技术映射（97.7%）
- 一句话重新定义（95.5%）
- 反直觉锚点（91.1%）

不稳定/可选机制：

- 视觉化推演（62.2%）
- 心理按摩/仪式感（75.5%）
- 生活比喻（80%，但在硬核论文时会弃用）

重要判断：原来的“六步法”过拟合了少数片段，后来改成三层模型：

- 核心方法：反差锚点、原子化拆解、极简定格
- 常用技巧：同构代换、视觉化推演、信息重组、公式拆解
- 风格包装：去圣化叙事、仪式感、名词诈骗揭露（不应过度写入 skill）

## 9. 已踩过的坑

1. 不要把飞天闪客的口癖写进 skill。
   - “闭上眼睛，清空大脑”太像角色扮演。
   - “摆烂”“牛马”“狠话”等不应作为通用规则。

2. 不要把“去魅”写成嘲讽。
   - 更稳妥的原则是“解释约束、权衡和设计动机”。

3. 不要固定所有概念都降到函数/数/开关。
   - 应寻找“最小可运行模型”。
   - 可能是数据流、状态变化、约束权衡、角色协作、数学变换等。

4. 不要要求比喻 1:1 映射每个元素。
   - 应做“关键结构映射”，并说明比喻边界。

5. 不要把生活比喻和视觉化推演机械二选一。
   - 可以组合，主路径取决于用户卡住的地方。

6. 不要让 NotebookLM 直接改 skill。
   - 让它做报告，Codex 把关。

## 10. 可能的后续工作

### A. 再跑一次 skill 验证

更新“文字化动态推演”后，可以让新窗口用全新概念测试，例如：

- Raft 共识算法是干啥的？
- Bloom Filter 是干啥的？
- 反向代理为什么存在？
- 标记-清除垃圾回收怎么工作？
- PageRank 为什么能给网页排名？

注意：不要用 skill 中已经出现过的概念来测试泛化，避免泄题。

评分仍用 14 分表，重点新增观察：

- 是否出现动作化降解
- 是否先追踪局部对象再推广整体
- 是否用步骤/分帧呈现状态变化
- 是否避免过度拟人化

### B. 进一步根据失败样本微调 skill

如果新测试出现问题，优先按失败样本改：

- 比喻很好但不映射：强化关键结构映射
- 过度故事化：强化“不要同时牺牲准确性”
- 不说明边界：把边界说明从建议改成更明确规则
- 术语太早出现：强化术语延迟
- 动态过程讲成静态定义：强化文字化动态推演

### C. 可考虑把 examples 做成 reference 文件

目前 skill 没有 references，只靠 SKILL.md。后续如果需要更强，可以新增：

- `references/examples.md`：存放好/坏案例和评分表
- `references/visual-inference-patterns.md`：存放文字化动态推演模式及例子

但不要急着加，除非验证发现 SKILL.md 太抽象，不足以稳定触发。

## 11. 关键文件清单

- Skill：`C:\Users\zhanbohan\.codex\skills\explain-complex-concepts\SKILL.md`
- Skill UI 元数据：`C:\Users\zhanbohan\.codex\skills\explain-complex-concepts\agents\openai.yaml`
- 验证输出目录：`D:\学习资料\explain`
- NotebookLM 当前输出：`D:\学习资料\lm.txt`
- YouTube URL 列表：`D:\学习资料\youtube_urls.txt`
- 字幕目录：`D:\学习资料\youtube_subtitles`（之前尝试过 yt-dlp 拉字幕，多数失败；用户后来转用 NotebookLM）
- Cookie 文件：`D:\学习资料\cookies.txt`（敏感登录凭证，避免读取/暴露内容）

## 12. 如果新窗口要继续修改 skill

建议流程：

1. 读取 `SKILL.md`（UTF-8）。
2. 给出修改方案，等待用户确认。
3. 写入时使用 UTF-8 无 BOM。
4. 运行：

```powershell
$env:PYTHONUTF8='1'; python "C:\Users\zhanbohan\.codex\skills\.system\skill-creator\scripts\quick_validate.py" "C:\Users\zhanbohan\.codex\skills\explain-complex-concepts"
```

5. 抽查插入位置，确认章节没有重复。
6. 最终回复简洁说明改了什么、校验结果。

## 13. 本轮特有的 skill 工程踩坑

这里只记录 AGENTS/CODEX 和 `skill-creator` 文档里不够显眼、但本轮实际踩过的坑。通用创建流程、命名规范、目录结构等请回到 `skill-creator` skill 本身，不在这里重复。

### 13.1 `short_description` 长度坑

生成 `agents/openai.yaml` 时，`short_description` 太短会失败：

```text
short_description must be 25-64 characters
```

已验证可用的描述：

```text
用最小模型、结构化比喻和逐步推演讲清各种复杂抽象概念
```

### 13.2 中文 SKILL.md + Windows Python 编码坑

Windows 下运行 `skill-creator` 脚本时，Python 可能按 GBK 读取中文 `SKILL.md`，导致：

```text
UnicodeDecodeError: 'gbk' codec can't decode byte ...
```

本轮解决方式是在运行校验/生成脚本前设置：

```powershell
$env:PYTHONUTF8='1'
```

### 13.3 PowerShell UTF-8 BOM 坑

用 `Set-Content -Encoding UTF8` 写 `SKILL.md` 后，frontmatter 可能被 BOM 污染，校验报：

```text
[ERROR] Invalid SKILL.md frontmatter format.
```

本轮有效写法：

```powershell
[System.IO.File]::WriteAllText($path, $content, [System.Text.UTF8Encoding]::new($false))
```

### 13.4 插入章节时的换行坑

本轮第一次插入“文字化动态推演”失败，因为匹配的是 CRLF：

```powershell
"`r`n## 禁忌"
```

但实际文件更接近 LF。后来改用：

```powershell
"`n## 禁忌"
```

并在插入前检查章节是否已存在，避免重复插入：

```powershell
if ($content -notlike "*## 文字化动态推演*") { ... }
```

### 13.5 初始化部分失败但目录已创建

本轮 `init_skill.py` 因 `short_description` 太短中途失败，但已经创建了：

```text
C:\Users\zhanbohan\.codex\skills\explain-complex-concepts\SKILL.md
```

这种情况下不要重复初始化同名 skill。应先检查目录，改写已有 `SKILL.md`，再单独补跑 `generate_openai_yaml.py`。

### 13.6 本轮最小复验命令

修改后至少跑：

```powershell
$env:PYTHONUTF8='1'; python "C:\Users\zhanbohan\.codex\skills\.system\skill-creator\scripts\quick_validate.py" "C:\Users\zhanbohan\.codex\skills\explain-complex-concepts"
```

期望输出：

```text
Skill is valid!
```

如改了 UI 元数据，再确认：

```text
C:\Users\zhanbohan\.codex\skills\explain-complex-concepts\agents\openai.yaml
```