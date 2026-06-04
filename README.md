# Fuck My Shit Mountain 🏔️💩

> 免责声明：AI 审查结果仅供娱乐和参考，不代表项目的实际质量、安全性、合规性或发布就绪度；任何结论都应结合人工审查、测试结果和真实运行环境验证。

> 基于证据的 AI 代码审计技能。专业输出。零情绪废话。

**Fuck My Shit Mountain** 是一个 AI 技能（提示词框架），用于生成严谨、专业的代码审查报告。名字虽然粗俗，但每一份报告都是冷静、结构化、证据驱动、可执行的。

## 工作流程

1. **AI 先问 3 个问题** — 选什么模式、报告用什么语言、输出格式（md/html/both/stdout）
2. **AI 穷尽审计你的代码库** — 每个文件、每个函数都不放过
3. **AI 生成结构化报告** — 评分、发现、原则合规、修复顺序、速赢项
4. **HTML 输出** — 带侧边栏导航 + 滚动监听、彩色评分条、各维度发现表 + 已验证清单、设计原则合规表、修复顺序表

## Demo 预览

如果你想直接给别人看一个“长得像真的”审查页面，可以看这个静态演示页：

- [`docs/index.html`](docs/index.html) 是 GitHub Pages 的入口页
- 页面顶部已经明确标注 `演示 / 虚构 / 非真实审计`
- 如果仓库的 Pages 源设置为 `main /docs`，推送后会自动发布；`.nojekyll` 已经放在 `docs/` 下

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

## 原生支持平台

当前这个仓库提供的是标准的 `SKILL.md + prompts + rubrics + templates` skill 目录，原生可用于以下工具：

### Codex

1. 将 `fuck-my-shit-mountain/` 整个目录复制到 `~/.codex/skills/fuck-my-shit-mountain/`
2. 重启 Codex，让它重新加载 skill 元数据
3. 在 Codex 对话里直接请求使用这个 skill

### Claude Code

1. 个人安装：复制到 `~/.claude/skills/fuck-my-shit-mountain/`
2. 项目安装：复制到 `.claude/skills/fuck-my-shit-mountain/`
3. 启动 `claude` 后，通过提示词或 `/fuck-my-shit-mountain` 调用

### GitHub Copilot（CLI / VS Code Agent / Cloud Agent）

1. 个人安装：复制到 `~/.copilot/skills/fuck-my-shit-mountain/`，或 `~/.agents/skills/fuck-my-shit-mountain/`
2. 项目安装：复制到 `.github/skills/fuck-my-shit-mountain/`、`.claude/skills/fuck-my-shit-mountain/`，或 `.agents/skills/fuck-my-shit-mountain/`
3. 在 Copilot CLI 中执行 `/skills reload`
4. 用 `/skills info fuck-my-shit-mountain` 确认已加载

### Gemini CLI

1. 个人安装：复制到 `~/.gemini/skills/fuck-my-shit-mountain/`，或 `~/.agents/skills/fuck-my-shit-mountain/`
2. 项目安装：复制到 `.gemini/skills/fuck-my-shit-mountain/`，或 `.agents/skills/fuck-my-shit-mountain/`
3. 在 Gemini CLI 中执行 `/skills reload`
4. 用 `/skills list` 确认 skill 已被发现
5. 如果使用项目目录安装，先确保工作区已 trust

如果你更新了仓库里的 skill 内容，把目录重新同步到对应工具的 skills 目录，再按各工具的刷新方式重新加载即可。

示例提示词：

```text
请使用 fuck-my-shit-mountain skill 审计当前项目
模式：full
报告语言：中文
输出格式：html
```

## License

MIT

---

学 AI 上 [LinuxDo](https://linux.do/)
