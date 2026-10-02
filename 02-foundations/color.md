# 02.1 — Color

> **Color should guide attention, not demand attention.**  
> 颜色应该引导注意力，而不是索取注意力。

## 颜色层级

```text
Neutral  中性色：背景、Surface、文本、边界
Brand    品牌色：识别、主要操作、选择、Focus
Semantic 语义色：Success / Warning / Error / Info
State    状态色：Hover / Pressed / Selected / Disabled
Material 材质色：Solid 温度、Glass Tint、Highlight
```

## 默认原则

- `Neutral First`：普通页面约 80–90% 由 Neutral / Surface 构成。
- 通常只有一个主要 Accent；辅助 Accent 不应与其竞争。
- 品牌色主要用于 Primary Action、Selection、Focus、关键状态和品牌识别。
- 低饱和不等于无色；关键状态仍要有足够辨识度。
- 渐变应像光，不像颜料；优先用于品牌、Hero、光照和材质变化，谨慎用于普通控件。
- 纯白和纯黑可用，但不作为所有大型 Surface 的默认值。
- 状态不能只靠颜色表达，至少结合图标、文字、形状或位置。

## Light / Dark

Light 通过细微明度差建立 `Canvas → Surface → Raised → Floating`；避免白卡叠灰底、强黑边和重阴影。

Dark 不是简单反色：Canvas 最暗，靠近用户的 Surface 逐级变亮；品牌色需单独调整亮度、饱和度和对比度。

## 语义角色

```text
color.canvas
color.surface.primary / secondary / raised / floating / overlay
color.text.primary / secondary / tertiary / disabled / inverse / on-accent
color.border.subtle / standard / strong / focus / error
color.action.primary / secondary / destructive
color.status.success / warning / error / info
```

## 色彩决策检查

加入颜色前，确认它承担明确职责、没有与既有颜色重复、不用颜色无法更好表达、不会破坏焦点，并且在 Light / Dark 下都成立。

## 当前数值基线

共享 token 1.0.0 提供以下基色；具体 Raised、Recessed 和六套色族按主题派生。此表不是所有状态/背景的对比度认证。

| 角色 | Light | Dark |
| --- | --- | --- |
| ink | #152232 | #EEF3FA |
| paper / canvas | #E9EEF4 | #101822 |
| surface | #F2F5F8 | #192431 |
| accent | #3978D0 | #8DBBFF |
| accentSoft | #DCE7F5 | #243D5D |
| muted | #637183 | #A3B3C5 |
| danger | #AC4545 | #FF8E91 |
| outline | #D8E0E5 | #344356 |

来源：[数值快照](../10-tokens/lumina.v1.json)。文字主体保持不透明；默认雕刻模式可叠加低对比细高光，清透模式移除蚀刻文字阴影。高对比场景优先可读文字与明确边界。
