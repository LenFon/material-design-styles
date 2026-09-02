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
├── references/
│   └── MD样式分类清单.md           # 完整命名样式清单（按 MD2 / MD3 / 已废弃分组）
├── LICENSE                        # MIT 许可证
└── .gitignore
```

## 用法

XAML 中直接引用命名样式：

```xml
<Button Style="{StaticResource MaterialDesignRaisedButton}" />
```

常用按钮变体：

- 实心带阴影：`MaterialDesignRaisedButton`
- 扁平无阴影：`MaterialDesignFlatButton`
- 描边透明底：`MaterialDesignOutlinedButton`
- 悬浮操作：`MaterialDesignFloatingActionButton`（支持 `Mini` / `Dark` / `Light` / `Secondary` 派生）

## 许可

本项目基于 [MIT 许可证](LICENSE) 开源。
