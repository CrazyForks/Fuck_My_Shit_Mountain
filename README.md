# Fuck My Shit Mountain 🏔️💩

> 基于证据的 AI 代码审计技能。专业输出。零情绪废话。

**Fuck My Shit Mountain** 是一个 AI 技能（提示词框架），用于生成严谨、专业的代码审查报告。名字虽然粗俗，但每一份报告都是冷静、结构化、证据驱动、可执行的。

## 工作流程

1. **AI 先问 3 个问题** — 选什么模式、报告用什么语言、输出格式（md/html/both/stdout）
2. **AI 穷尽审计你的代码库** — 每个文件、每个函数都不放过
3. **AI 生成结构化报告** — 评分、发现、原则合规、修复顺序、速赢项
4. **HTML 输出** — 带侧边栏导航 + 滚动监听、彩色评分条、各维度发现表 + 已验证清单、设计原则合规表、修复顺序表

## 模式

可选单个或组合（如 `security, stability, type-safety`）。Full 模式覆盖 **19 个审计维度**。

| 模式 | 聚焦 |
|------|------|
| `full` | 全部 19 个维度 |
| `security` | 认证、注入、密钥、依赖 |
| `stability` | Panic 路径、错误处理、并发、生命周期 |
| `performance` | 热点路径、内存、I/O、启动开销 |
| `testing` | 测试覆盖率、测试类型、脆性 |
| `maintainability` | 复杂度、耦合、重复、命名 |
| `release` | CI/CD、版本管理、升级、回滚 |
| `fallback` | 静默降级、空 catch、防御性猜测 |
| `testing-authenticity` | 过度 Mock、实现细节测试、虚假信心 |
| `type-safety` | Unsafe 块、类型断言、边界类型 |
| `frontend-state` | 组件大小、状态重复、副作用、耦合 |
| `backend-api` | API 一致性、校验、N+1、数据流 |
| `dependency-weight` | 过重依赖、构建工具链 |
| `code-consistency` | 命名、导入、模式、风格统一性 |
| `comment-coverage` | 文档质量、过期注释、缺失文档 |

## 项目结构

```
fuck-my-shit-mountain/
├── SKILL.md              — 入口点 & 规则
├── prompts/              — 15 个审计模式提示词
├── rubrics/              — 严重程度、置信度、证据、原则、评分
├── templates/            — audit-report.md, audit-report.html, issue-card.md, remediation-plan.md
└── examples/             — Rust、Node.js、Vue 审计示例
```

## 评分面板示例

```
Security        ████████░░  8.0  A
Stability       ██████░░░░  6.0  B
Performance     ██████████  10.0 S
Testing         ████░░░░░░  4.0  C
Maintainability ███████░░░  7.0  A
Design          █████░░░░░  5.0  B
Release         ██████░░░░  6.0  B
─────────────────────────────────────
Overall         ██████░░░░  6.6  B
```

**越高越好（10 = 干净，0 = 屎山）。** 评分基于判断而非公式计算。

详见 `fuck-my-shit-mountain/rubrics/scoring.md`。

## 各 AI 工具安装方式

### Codex（已配置元数据）

项目已包含 Codex 配置，可直接加载 skill：

```
/code
请使用 fuck-my-shit-mountain skill 审计当前项目
```

或在 Codex 中引用 SKILL.md：

```
load fuck-my-shit-mountain/skill.md
run full-audit on .
```

### Claude Code

```bash
# 在项目目录中运行
claude
```

然后在对话中引用：

```
请使用 fuck-my-shit-mountain skill 进行 full 审计
输出格式 html
```

### Cursor / Superpower / 其他 AI IDE

将 `SKILL.md` 作为 system prompt 加载，然后输入：

```
Use the fuck-my-shit-mountain skill in full mode.
Audit this repository for stable release readiness.
Output format: html with Chinese report
```

### 手动使用

1. 打开 `fuck-my-shit-mountain/SKILL.md` 了解规则
2. 根据需求选择 `prompts/` 下对应的审计模式
3. 将提示词 + 代码库内容粘贴到任意 AI
4. AI 会先问 3 个问题，然后开始审计

## License

MIT

---

学 AI 上 [LinuxDo](https://linux.do/)
