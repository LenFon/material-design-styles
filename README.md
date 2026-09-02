# material-design-styles

WorkBuddy 技能：MaterialDesignInXamlToolkit（WPF）命名样式参考与控件样式选型指南。

基于最新稳定版 **v5.3.2**（NuGet `MaterialDesignThemes` / `MaterialDesignColors`，目标框架 .NET 10）。

## 内容

- `SKILL.md`：版本要点、架构说明、MD2/MD3 变体派生规律、快速选型示例，以及「维护与月度更新流程」。
- `references/MD样式分类清单.md`：405 个唯一命名样式（`x:Key`）完整清单，按 Material Design 2.0（共享核心）/ 3.0（专属新增）/ 已废弃分组，含样式键、目标类型、中文说明、继承自。

## 适用场景

WPF / MaterialDesignThemes（`.Wpf` 或 `.MahApps`）项目中需要「选样式」「配色」「Raised/Flat/Outlined/FloatingHint/Filled 变体」「MD2 vs MD3」时使用。

## 维护

至少每月校验一次 NuGet 最新稳定版；仅认生产可用稳定版，不纳入预发布。详见 `SKILL.md`。

## 用法

在 WorkBuddy 对话中调用此技能即可获得样式选型建议；命名样式通过 `Style="{StaticResource <Key>}"` 引用。
