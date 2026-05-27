# 更新日志

## v0.4 — 写在前面章节完工（2026-05-27）

### 新增

- preface/index.md：补充手册来源、三模块设计思路、子章节导航卡片

### 修复

- 解决 docs/index.md 的 Git 合并冲突，保留正确 frontmatter

## v0.3 — 首页排版优化（2026-05-27）

### 优化

- 暗色模式 hero 标题渐变调亮（`#b39ddb → #ffcc80`），提升对比度
- Hero 按钮圆角统一为胶囊形（`999px`）
- `section-heading` 装饰短线宽度改为 `3em`，随字号自适应
- `question-list` 徽章字体改为 `inherit`，与全站无衬线风格一致
- `meta-info-item` 圆角从 `4px` 升至 `8px`，与卡片风格统一
- 新增平板断点（768px），hero 标题缩小至 `2.1rem`

## v0.2 — 概念地图全章完工（2026-05-27）

### 新增

- 概念地图 index：阅读路径 + 七概念关系图
- 1.1 大模型基础（Embedding vs 生成、上下文窗口、Token、幻觉防御）
- 1.2 Agent 与 Harness Engineering（Agent 四组件 + 6 大 Harness 对比）
- 1.3 Prompt 与 Context Engineering（五大杠杆 + 经济学 Context 配方）
- 1.4 RAG 与知识库（三档库策略 + 学术 RAG 三特殊要求）
- 1.5 Skill 的本质（vs Prompt 模板 + 起步建议）
- 1.6 MCP 与 API（工作原理 + 经济学场景 + 必装 3 个 MCP）
- 1.7 Vibe Coding 的边界（Vibe 度按任务分级 + 半 vibe 工作流）
- 元说明：本书是怎么用 AI 写的（人机协作工作流 + 迭代日志）

### 修复

- 移除全部个人隐私信息（真名、学校、个人主页、本地路径、端口号）
- 统一作者身份为 "CleverLsy"

## v0.1 — 仓库初始化（2026-05-27）

### 新增

- MkDocs Material 主题骨架（中文支持、明暗模式、Noto Sans SC 字体）
- 完整 7 模块大纲（概念/工具/Pipeline/Skill/案例/边界/附录）
- 49 个章节占位文档
- GitHub Actions 自动部署 workflow
- mkdocs-jupyter 插件支持（案例库章节用）
- README、LICENSE（CC BY-NC-SA 4.0）、.gitignore
- 同步 demo 单页文档（约 1.4 万字）

### 验证

- 本地 mkdocs build --strict 通过（0.46s 无错）
- 本地预览 HTTP 200
