# Demo Audit Pages Design

## 目标

为仓库补一份“明显是演示版”的假审查页面，用来展示 `Fuck My Shit Mountain` 的报告格式，并通过 GitHub Pages 对外公开。

页面必须一眼看出是 demo，不得冒充真实审计结果。

## 范围

### 要做

- 新增一个可直接被 GitHub Pages 发布的静态页面。
- 页面内容按照现有审计模板组织，包含评分面板、概述、统计、风险项、详细发现、原则、修复顺序和速赢项。
- 内容全部使用虚构数据，模拟一次完整的“审查报告”。
- 在页面顶部和页脚都明确标注 `DEMO / FAKE / NOT A REAL AUDIT`。
- 在根 `README.md` 增加 demo 入口说明，方便用户快速找到页面。

### 不做

- 不接入真实代码分析。
- 不新增构建工具链。
- 不改动 skill 的实际审计逻辑。
- 不做多页面站点，不做账号系统，不做交互式编辑器。

## 方案

采用最省事的静态站点方案：

- 发布目录使用 `docs/`
- 入口文件使用 `docs/index.html`
- 必要时增加 `docs/.nojekyll`
- 直接复用 `fuck-my-shit-mountain/templates/audit-report.html` 的视觉结构和排版逻辑

选择这个方案的原因：

- GitHub Pages 能直接从 `main` 分支的 `docs/` 目录发布。
- 不需要额外构建步骤。
- 页面结构和现有模板一致，最容易展示这个项目的审计风格。

## 页面内容

demo 页面使用一个虚构项目，例如 `demo-checkout-service`，但所有发现都必须是合成内容。

页面结构保持模板风格，至少包含：

- 顶部明显的 demo 警示条
- 项目信息和日期
- 7 个评分卡
- 执行摘要
- 发现统计
- Top Risks
- 详细发现
- 各维度分析
- 原则合规
- 修复顺序
- 速赢项

建议放入 5-8 条虚构发现，覆盖不同严重程度，让页面看起来完整但不会误导用户。

## 文件布局

- `docs/index.html`：静态 demo 页面
- `docs/.nojekyll`：如有需要，用于避免 GitHub Pages 的 Jekyll 处理
- `README.md`：补充 demo 入口和 Pages 说明

## 发布方式

GitHub Pages 采用 `main` 分支的 `docs/` 目录作为 publishing source。

仓库代码只负责准备静态内容；Pages 开关和 source 需要在 GitHub 仓库设置中指向 `main /docs`。

## 验证标准

- `docs/index.html` 能直接在浏览器打开
- 页面顶部清楚写明这是 demo，不是实际审查
- 页面布局在桌面和移动端都能正常显示
- README 能让人快速找到 demo 页面
- 不存在会让人误以为这是真实 audit 的措辞

## 风险

- 页面如果没有足够强的 demo 标识，容易被误读为真实审查。
- GitHub Pages 可能还需要一次性手动启用 source 配置。
- 如果以后模板结构变化，demo 页面需要同步更新，避免样式漂移。

## 验收

完成后，仓库应具备：

1. 一个公开可展示的 demo 审查页面。
2. 清晰的免责声明和 demo 标识。
3. 最小化的发布路径，优先保证省事和可维护。
