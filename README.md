# Fuck My Shit Mountain 🏔️💩

给 Codex、Claude Code、Copilot、Gemini 这类 AI coding agent 用的代码库审计 skill。

它会先摸清项目结构，再按你选的方向生成审计报告：风险在哪里、证据是什么、为什么重要、先修什么、怎么补测试。名字是玩笑，报告尽量认真。

提醒一下：AI 审计只能当参考，结论最好结合人工 review、测试结果和真实运行环境一起判断。

## 怎么审

1. 先问清楚模式、报告语言和输出格式；如果你没选模式，会先扫一眼项目结构，再用你的语言推荐几个方向。
2. 看项目源码、测试、配置、依赖、CI、发布文件和文档，报告里会写清楚看过什么、没看什么。
3. 输出评分、发现、证据、影响、修复顺序、速赢项和回归测试建议。
4. 需要 HTML 的话，会生成一个能直接打开的报告页，带侧边栏、评分条、发现表和修复计划。

## Demo

这里有一份静态演示页，可以先看看报告长什么样：

[https://xinian-dada.github.io/Fuck_My_Shit_Mountain/](https://xinian-dada.github.io/Fuck_My_Shit_Mountain/)

演示内容是虚构审计，页面顶部也有标注。

## 模式

你可以直接说“全量审计”“偏安全与隐私”“偏前端体验”“偏发布与运维”。skill 会把这些说法映射到内部模式。

熟悉以后，也可以直接写 mode 名，比如 `security, stability, type-safety`。`full` 会覆盖 **25 个审计维度**。

| 模式 | 聚焦 |
|------|------|
| `full` | 全部 25 个维度 |
| `architecture` | 架构边界、依赖方向、状态所有权 |
| `security` | 认证、注入、密钥、依赖 |
| `stability` | Panic 路径、错误处理、并发、生命周期 |
| `performance` | 热点路径、内存、I/O、启动开销 |
| `testing` | 测试覆盖率、测试类型、脆性 |
| `maintainability` | 复杂度、耦合、重复、命名 |
| `design` | 工程原则和设计风险 |
| `release` | CI/CD、版本管理、升级、回滚 |
| `documentation` | 文档准确性、设置、运维/开发指南 |
| `observability` | 日志、指标、追踪、健康检查、告警 |
| `configuration` | 配置校验、默认值、环境隔离、功能开关 |
| `data-integrity` | 事务、幂等、迁移、一致性、备份恢复 |
| `privacy` | PII、数据最小化、保留、删除、导出 |
| `accessibility` | 键盘、焦点、语义、响应式和 UX 状态 |
| `supply-chain` | 依赖来源、可复现构建、CI 完整性、签名 |
| `cost` | 资源经济性、预算、外部 API 和 LLM 成本 |
| `ai-safety` | Prompt injection、工具授权、RAG 泄露、eval |
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
├── agents/               — UI metadata
├── prompts/              — 26 个审计模式提示词
├── references/           — 公共报告格式、HTML、coverage、lint、工具参考
├── rubrics/              — 严重程度、置信度、证据、原则、评分
├── scripts/              — 项目画像、报告 lint、校验脚本
├── templates/            — audit-report.md, audit-report.html, issue-card.md, remediation-plan.md
└── examples/             — Rust、Node.js、Vue 审计示例
```

## 安装与更新

复制这一行就行。安装和更新都用它：

### Codex 一行安装 / 更新

```bash
tmp="$(mktemp -d)" && git clone --depth=1 https://github.com/XiNian-dada/Fuck_My_Shit_Mountain.git "$tmp" && mkdir -p ~/.codex/skills && rm -rf ~/.codex/skills/fuck-my-shit-mountain && cp -R "$tmp/fuck-my-shit-mountain" ~/.codex/skills/fuck-my-shit-mountain && rm -rf "$tmp"
```

然后重启 Codex，或者新开一个对话。

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

## 支持平台

仓库里提供的是标准 `SKILL.md + prompts + rubrics + templates` 目录，可以放进这些工具的 skills 目录里。

### Codex

1. 推荐用上面的 “Codex 一行安装 / 更新” 安装到 `~/.codex/skills/fuck-my-shit-mountain/`
2. 重启 Codex 或新开对话
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

更新 skill 时，重新执行上面的一行安装命令，再按对应工具的刷新方式重载。

示例提示词：

```text
请使用 fuck-my-shit-mountain skill 审计当前项目
模式：full
报告语言：中文
输出格式：html
```

## Star History

<a href="https://www.star-history.com/#XiNian-dada/Fuck_My_Shit_Mountain&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=XiNian-dada/Fuck_My_Shit_Mountain&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=XiNian-dada/Fuck_My_Shit_Mountain&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=XiNian-dada/Fuck_My_Shit_Mountain&type=Date" />
  </picture>
</a>

## License

MIT

---

学 AI 上 [LinuxDo](https://linux.do/)
