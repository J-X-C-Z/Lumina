# 10.6 — Material Tokens

```text
material.solid
material.solid.base
material.solid.card
material.solid.raised
material.solid.floating

material.glass
material.glass.thin
material.glass.standard
material.glass.dense
material.glass.fitted
material.glass.floating

material.topography.flat
material.topography.embedded
material.topography.raised
material.topography.recessed
material.topography.scored

elevation.canvas
elevation.base
elevation.content
elevation.fitted
elevation.floating
elevation.overlay

shadow.contact
shadow.low
shadow.medium
shadow.high

glass.tint
glass.highlight
glass.refraction
glass.trace
glass.ripple
glass.etched-ink
```

这些 Token 表达角色与强度，不预设所有平台必须使用同一实现；Web、Mobile、Desktop 和 Watch 可以按性能与系统能力降级。

## 实现映射限制

雕刻/清透是外观模式，与性能模式独立。JSON glass.blur=12、highPerformanceBlur=6 不是 Flutter 实际 sigma：当前 Flutter Gaussian 档位为0/3.5/5.5/9/14；Web 使用 CSS 映射。`glass.trace/refraction/ripple` 等语义名是设计能力架构，不代表 Flutter 已实现真实折射或水波。完整策略见 [Flowing Glass](../03-materials/flowing-glass.md) 和 [Flutter](../08-platforms/flutter.md)。

## v0.3 外观与成本

补充 `neumorphic` / `neumorphicGlass` 平台配置，保留默认雕刻与清透分支。高性能 Surface 使用静态磨砂、九宫格缓存阴影；显式 backdrop 选择井可继续使用其独立策略。连续压力采用固定遮罩混合，不让缓存 key 随每帧压力增长。详见[材质基线](../03-materials/neumorphic-glass.md)。
