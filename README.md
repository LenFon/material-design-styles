# material-design-styles

WorkBuddy 技能：MaterialDesignInXamlToolkit（Material Design In XAML Toolkit）命名样式参考与 WPF 控件样式选型指南。

## 用途

在 WPF / Material Design 项目中需要「选样式」「配色」「Raised / Flat / Outlined / FloatingHint / Filled 变体」「MD2 vs MD3」时使用。基于最新稳定版源码整理，跨文件同名键已按主定义文件归并。

## 校验版本

- **v5.3.2**（最新稳定版；NuGet `MaterialDesignThemes` / `MaterialDesignColors` 5.3.2，目标框架 .NET 10）
- 命名样式统计（去重后唯一）：**405** 个
  - Material Design 2.0（经典 / 共享核心）：350
  - Material Design 3.0（专属新增）：28
  - 已废弃（非 2.0 / 3.0）：25
  - 默认映射：2

## 目录结构

```
material-design-styles/
├── SKILL.md                       # 技能说明（锁定版本、用法、版本要点）
└── references/
    └── MD样式分类清单.md           # 完整命名样式清单（按 MD2 / MD3 / 已废弃分组）
```

## 用法

XAML 中直接引用命名样式：

```xml
<Button Style="{StaticResource MaterialDesignRaisedButton}" />
```

MD3 默认外观由 `MaterialDesign3.Defaults.xaml` 映射，MD2 由 `MaterialDesign2.Defaults.xaml` 映射。

## 版本要点（优先使用最新版）

- v5.3.1：新增 `StatusBar` 默认样式，将 `material-color-utilities` 移植到 dotnet（动态调色板更准）。
- v5.3.2：为 `Clock` 增加 `MinuteSelectionStep` 属性。
- 已移除 / 禁止再用的旧键名：`MaterialDesignRichTextBox`、`MaterialDesignScrollViewer`、`MaterialDesignWindow`、`MaterialDesignOutlinedComboBox`、`MaterialDesignToolBarToggleButton`、MD3 `NavigationBar*` / `NavigationRail*` 的 ListBox 派生样式、Snackbar 动作按钮变体（`MaterialDesignSnackbarAction*Button`）等。
