# 1.5 Skill 的本质

## 一句话理解

**Skill** = 一份让 AI **"按这个套路办事"** 的可复用、可共享、可迭代的说明书。

它不是 Prompt 模板（虽然很像），不是 Function（虽然能被调用），而是介于两者之间——**结构化的工作流知识**。

## 从 Prompt 模板到 Skill：一次进化

研究者用 AI 的常见演化路径：

### Stage 1：手写每次提示词

```
"帮我精读这篇论文，提取研究问题、数据、识别策略、结论"
（每次写论文都重复一遍）
```

### Stage 2：建 Prompt 模板库

```markdown
[精读模板.md]
# 论文精读模板

请按以下结构提取：
- 研究问题
- 数据来源
- 识别策略
- 主要结论
- 局限性

输入：[这里贴 PDF]
```

每次复制粘贴用。**已经比 Stage 1 好很多**，但还是要手动调用。

### Stage 3：进化为 Skill

```yaml
---
name: econ-paper-notes
description: 经济学论文精读笔记，支持实证/理论/混合三种模式
when_to_use: |
  用户提到"精读"、"读这篇论文"、"提取要点"、"做笔记"
  或上传论文 PDF
license: complete
---

# 经济学论文精读

## 触发条件
（明确何时激活，AI 自己判断）

## 步骤
1. 识别论文类型（实证/理论/混合）
2. 按对应模式提取
3. 标注每条结论的原文页码
4. 输出到 Obsidian 文献笔记目录

## 模式 A：实证论文
- 研究问题
- 识别策略（DID/IV/RDD）
- 数据：来源、样本量、时间跨度
- 主回归结果（系数、显著性、解释）
- 稳健性检验
- 异质性分析

## 模式 B：理论论文
...

## 避坑
- 公式如果是图片格式，必须人工誊抄
- 表格里的数字 AI 容易看错，关键数据回原文核对
- "贡献"段落 AI 倾向于美化，谨慎引用

## 验证
完成后回答三个问题：
1. 这篇文章如果只能用一句话总结，是什么？
2. 它的最关键创新在哪？
3. 它对你的研究有什么具体启发？
```

**Skill 不只是模板，它是一份完整的工作流知识包**。

## Skill 与 Prompt 模板的本质区别

| 维度 | Prompt 模板 | Skill |
|---|---|---|
| 触发方式 | 你手动复制粘贴 | AI **自己判断**何时使用 |
| 内容 | 一段提示词文本 | 触发条件 + 步骤 + 避坑 + 验证 + 工具调用 |
| 状态 | 静态文本 | **可执行**（嵌入工具调用） |
| 进化 | 改一次是一次 | 用一次发现一个坑，**回写**到 Skill |
| 共享 | 复制粘贴给同事 | Git 仓库管理，**版本化共享** |
| 组合 | 难 | 多个 Skill 可以**串联**成 Pipeline |

最大的差别：**Skill 是 AI 主动加载的，不是你手动喂的。**

## Skill 的核心结构

一个最小可用的 SKILL.md：

```markdown
---
name: skill-name           # 唯一标识
description: 一句话说清干啥  # 让 AI 决定何时使用
when_to_use: |             # 触发条件，越具体越好
  用户提到 X / Y / Z
  或者出现 A 这种文件
---

# 标题

## 目标
（一段文字说清楚这个 Skill 要达到什么）

## 触发条件
（什么场景下激活）

## 步骤
1. ...
2. ...
3. ...
（步骤要可验证、可回溯）

## 避坑
- 坑 1：现象 + 怎么避
- 坑 2：现象 + 怎么避
（这是 Skill 最值钱的部分——你踩过的坑别人不用再踩）

## 验证
完成后怎么知道做对了？
（自查清单）
```

## Skill 的真正价值：经验沉淀

Skill 比 Prompt 模板**强在哪**？三个关键差别：

### 1. 经验回写

每次用 Skill 发现一个坑，**改回 Skill**。下次自动避开。

我自己 `econ-paper-notes` 的演化：

- v1：基本框架
- v2：加了"区分实证/理论/混合"——发现一刀切结构对理论文章不适用
- v3：加了"标注原文页码"——发现 AI 给的引用没法核查
- v4：加了"贡献段落谨慎对待"——发现 AI 倾向于美化作者贡献

**每一次迭代，都是一次研究经验的固化。**

### 2. 团队共享

Skill 是结构化的**研究方法 SOP**：

- 写好的 Skill 可以分享给学生、合作者
- 自己换电脑、换工具，Skill 跟着走
- 实验室级别可以建 Skill 库

### 3. 自动调用

最好的 Skill 你**根本意识不到它在工作**。

例：你说"帮我读这篇论文"——AI 自动加载 econ-paper-notes 并执行，你不用每次说"请按 X 步骤"。

## Skill 在哪里能找到

### 现成 Skill 资源库

| 资源 | 主打方向 | 备注 |
|---|---|---|
| [ClawHub](https://clawhub.dev/) | 通用 | 开源，量大 |
| [腾讯 SkillHub](https://skillhub.cn/) | 中文场景 | 国内可访问 |
| [psantanna/claude-code-my-workflow](https://psantanna.com/claude-code-my-workflow/) | 经济学专用 | Pedro Sant'Anna 的工作流 |
| [openecon.ai](https://openecon.ai/) | 经济学专用 | Skill + 工具集合 |
| [hsantanna.org/clo-author/](https://hsantanna.org/clo-author/) | 写作合作者 | 学术写作专用 |

### 适用范围

不同 Harness 对 Skill 的支持：

| Harness | Skill 支持 |
|---|---|
| Claude Code | ✅ 原生支持，最强 |
| Hermes | ✅ 原生支持 |
| Cursor | ⚠️ 通过 .cursorrules 实现类似功能 |
| ChatGPT GPTs | ⚠️ 类似但封闭 |
| 普通 ChatGPT/Claude.ai | ❌ 需要每次手动粘贴 |

## 经济学研究者的 Skill 起步建议

**不要一上来想做 50 个 Skill**。从最痛的工作流开始：

### 第一批（必备 5 个）

1. **econ-paper-notes**：论文精读
2. **literature-search**：文献检索
3. **stata-regression** / **r-econometrics**：你常用的实证语言
4. **academic-writer**：学术写作（中文/英文）
5. **journal-match**：投稿期刊匹配

### 第二批（按需扩展）

- 数据清洗（按你常用工具）
- 学者画像构建
- 财经新闻摘要
- 备课 PPT 生成
- 回应审稿人

详见 [自己写 Skill](../skills/index.md) 章节。

## 给经济学研究者的核心要点

1. **Skill 不是 Prompt 模板**，是结构化、可执行、可迭代的工作流知识
2. **核心价值在经验回写**：每次用都让它变好一点
3. **不是所有工具都支持 Skill**，Claude Code / Hermes 原生支持
4. **从最痛的工作流开始**，不要追求一次做全
5. **公开 Skill 资源库已有不少**，先抄再改

下一节：让 Skill 和 Agent 能调用真实世界工具的协议——**MCP**。

---

[:octicons-arrow-left-24: 1.4 RAG 与知识库](rag.md) · [下一节：1.6 MCP 与 API :octicons-arrow-right-24:](mcp-api.md)
