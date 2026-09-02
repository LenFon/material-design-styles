---
name: material-design-styles
description: MaterialDesignInXamlToolkit 命名样式参考与 WPF 控件样式选型指南（基于最新稳定版 v5.3.2）。按 MD2/MD3 分组复用 405 个唯一命名样式（x:Key）清单，覆盖按钮、输入框、卡片等控件变体。当用户在 WPF / Material Design 项目中需要「选样式」「配色」「Raised/Flat/Outlined/FloatingHint/Filled 变体」「MD2 vs MD3」时使用。
agent_created: true
---

# MaterialDesign 样式参考 Skill

适用：WPF / MaterialDesignThemes（`.Wpf` 或 `.MahApps`）项目的控件样式选型与 XAML 编写。

## 版本（优先使用最新版）
- **当前校验版本：v5.3.2**（最新稳定版；NuGet `MaterialDesignThemes` / `MaterialDesignColors` 5.3.2，目标框架 **.NET 10**）。
- 安装：`Install-Package MaterialDesignThemes`（或 `MaterialDesignThemes.MahApps`）。
- 写 XAML 默认以 v5.3.2 的命名样式为准；旧版本（v4.x 及更早）的样式键与本节清单可能不一致，**不要混用旧键名**。
- v5.3.x 要点：v5.3.1 新增 `StatusBar` 默认样式、将 `material-color-utilities` 移植到 dotnet（动态调色板更准）；v5.3.2 为 `Clock` 增加 `MinuteSelectionStep` 属性。
- 已移除/合并、禁止再用的旧键名示例：`MaterialDesignRichTextBox`、`MaterialDesignScrollViewer`、`MaterialDesignWindow`、`MaterialDesignOutlinedComboBox`、`MaterialDesignToolBarToggleButton`、MD3 `NavigationBar*`/`NavigationRail*` 的 ListBox 派生样式、Snackbar 动作按钮变体（`MaterialDesignSnackbarAction*Button`）等。

## 核心约定（长期使用）
凡使用 `MaterialDesignThemes` 创建 WPF 程序，**先看样式参考、再写 XAML**：优先选用命名样式（`x:Key`）以 `StaticResource` 引用，按 MD2/MD3 分组选取合适变体，并遵循对应 `Defaults` 映射。

## 架构要点
- 样式两大类：① 隐式默认样式（仅 `TargetType`、无 `x:Key`，由 `*Defaults.xaml` 自动套用）；② 命名变体样式（带 `x:Key`，需 `StaticResource` 引用）。
- MD3 **不另写控件**，而是「复用 MD2 核心控件库 `MaterialDesignTheme.*`（共享基础）+ 叠加 MD3 专属文件 `MaterialDesign3.*`」。
- 默认外观映射：`MaterialDesign2.Defaults.xaml`(MD2) / `MaterialDesign3.Defaults.xaml`(MD3)。
- 变体派生规律：`Raised` → `Flat` → `Outlined` → `FloatingHint` → `Filled`，辅以 `Mini` / `Reveal`(密码显隐) / `Discrete`(离散刻度) / `Switch`(开关)；可叠加 `Light`/`Dark`/`Primary`/`Secondary` 配色前缀。

## 样式统计（共 405 个唯一命名样式，已对 v5.3.2 去重）
| 分组 | 数量 | 说明 |
|---|---|---|
| MD2 共享核心 | 350 | `MaterialDesignTheme.*` + `MaterialDesign2.Defaults`（MD3 复用的键计入此处） |
| MD3 专属新增 | 28 | `MaterialDesign3.*` 新组件/排版（仅 MD3 文件独有的键） |
| 已废弃 | 25 | `ObsoleteStyles`（Accent 系列） |
| 默认映射 | 2 | `MaterialDesign2.Defaults` / `MaterialDesign3.Defaults` 中的映射键 |

> 注：源码中跨文件同名键已按「主定义文件」归并，故唯一键数（405）小于原始 `<Style x:Key>` 元素总数（446）。框架内部键（`ComponentResourceKey` / `x:Static ...StyleKey`）不计入。

## 完整清单
完整 405 个命名样式（含 样式键 / 目标类型 / 中文说明 / 继承自）见：

`references/MD样式分类清单.md`

用法：命名样式通过 `Style="{StaticResource <Key>}"` 引用。

## 快速选型示例（按钮）
- 实心带阴影：`MaterialDesignRaisedButton`
- 扁平无阴影：`MaterialDesignFlatButton`
- 描边透明底：`MaterialDesignOutlinedButton`
- 悬浮操作：`MaterialDesignFloatingActionButton`（支持 `Mini`/`Dark`/`Light`/`Secondary` 派生）

## 维护与发布（长期有效）
本技能有「本地技能目录」与「GitHub 发布副本」两份来源，更新需同步维护。

### 目录与仓库
- 本地技能目录：`C:\Users\PC\.workbuddy\skills\material-design-styles\`（`SKILL.md` + `references/MD样式分类清单.md`）
- GitHub 发布副本（独立 git 仓库）：`C:\Users\PC\material-design-styles\`
  - 远程：`https://github.com/LenFon/material-design-styles.git`
  - **默认分支 `main`**（远程 `master` 已删除）；推送走 HTTPS，复用本机 Windows 凭据管理器已存的 github.com 凭据
- 每月巡检自动化已配置（每月 5 日 09:00，ID `e3280c3f-da4c-4bb1-8a4d-d60c1c09a2b3`），自动查新稳定版并执行下列流程

### 版本更新流程（有新稳定版时）
1. **查最新稳定版**：NuGet 上 `MaterialDesignThemes` / `MaterialDesignColors` 的最新稳定版（仅稳定版，**禁** preview/alpha/beta/rc），对比当前锁定版本。
2. **下载源码**：`https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/archive/refs/tags/v<X.Y.Z>.tar.gz`，解包后在 `src/MaterialDesignThemes.Wpf/Themes/` 下处理。
3. **重新生成清单**（务必 XML 严格解析，勿用行级正则，避免漏跨行 `<Style>`）：
   - 提取所有带 `x:Key` 的 `<Style>` 元素；**剔除** `ComponentResourceKey` / `x:Static ...StyleKey` 等框架内部键；
   - **跨文件同名键按「主定义文件」归并**：优先 `MaterialDesignTheme.*`（非 Obsolete）→ `MaterialDesign3.*` → `Obsolete` → `Defaults`；MD3 复用 MD2 核心的键计入 MD2；
   - 按源文件/设计语言分三组输出：**A. MD2 核心** / **B. MD3 专属新增** / **C. 已废弃**，每组更新速览计数（去重后唯一键数 < 原始 `<Style x:Key>` 元素总数）。
4. **更新文件**：
   - `references/MD样式分类清单.md`：按 v5.3.2 格式重生成（速览表 + A/B/C 三组）；复用原中文说明，原占位「命名样式」条目据键名+目标类型补全。
   - `SKILL.md`：顶部 frontmatter 描述版本号、版本要点、命名样式总数（见「样式统计」表）。
5. **同步发布**：将更新后的 `SKILL.md`、`references/MD样式分类清单.md` 复制到 `C:\Users\PC\material-design-styles\`，并执行 `git add -A && git commit && git push origin main`。

> 坑位备忘：本机沙箱内 `git rebase`（尤其 `--root`/`--onto`）会破坏 `.git` 目录，需重做提交时直接 `git init -b main` 后 `--force` 推送，勿走 rebase；改 GitHub 默认分支用 API（`PATCH /repos/{owner}/{repo}` 带 `{"default_branch":"main"}`，Bearer 凭据），改完再删旧分支。
