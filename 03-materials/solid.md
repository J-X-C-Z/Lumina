# 03.2 — Solid

**Solid Material — 固态材质**是具有明确厚度、硬度和稳定性的内容承托材质。它不是纸张、玻璃或普通纯色矩形，而是一块经过精密加工的硬质数字薄板。

## 职责

Solid 承载文字、图片、数据、任务、消息、项目、文件、摘要、设置和可视化。它是 `Content Surface`，不是默认的 `Interaction Surface`。

```text
Solid Card       Rigid · Matte · Stable · Readable
Flowing Glass   Fluid · Glossy · Responsive · Interactive
```

Solid 的拓扑层级仍是内容结构的语义基础：Canvas、Solid、Raised、Recessed 各自表达稳定的承托、分组与层级。清透液态玻璃可以作为 Calm 内容结构中的容器或局部表面；它不取代 Solid 的内容职责，也不抹去底层拓扑关系。默认雕刻玻璃则保留细微纹理与蚀刻文字感。

## 视觉构成

- 有厚度：通过 Edge、Micro Bevel、Surface Light、Ambient Occlusion 和 Layer Separation 表达。
- 哑光：以 Diffuse Reflection 为主，不用镜面亮斑影响阅读。
- 有温度：可以是 Warm White、Cold White、Graphite、Slate、Blue Gray、Muted Green、Muted Sand 等低饱和材质色。
- 边缘明确但不锋利；可有约 1–3px 的视觉侧边厚度，但不做明显拟物挤出。
- 微纹理可以存在，但只让纯色不那么数字化，不应明显看出 Noise。

Light 中 Canvas 略深、Solid 略亮、Raised 再略亮；Dark 中 Canvas 最暗、Solid 稍亮、Raised 进一步提升。Solid Card 阴影比 Glass 更明确但仍柔和、低透明、不偏黑。Lumina 的 Light 基础色为 Ink `#152232`、Paper `#E9EEF4`、Surface `#F2F5F8`、Accent `#3978D0`、Muted `#637183`、Danger `#AC4545`、Outline `#D8E0E5`；Dark 对应 Ink `#EEF3FA`、Paper `#101822`、Surface `#192431`、Accent `#8DBBFF`、Muted `#A3B3C5`、Danger `#FF8E91`、Outline `#344356`。命名 Palette tint 会参与派生 raised/recessed surface 与 accent，不应把这些基础值误读为每种 palette 的最终颜色。

## 内容与交互分工

文字像精准印刷在表面上，主要依赖 Typography、Spacing、Color 建立层级。Card 本身默认几乎不流动；可交互 Card 只做轻微 Elevation、亮度或边缘变化，避免水痕、涟漪和强 Scale。

操作按钮、More、Edit、Confirm、Filter、Toolbar 等可以在 Solid 上使用 Flowing Glass，形成：

```text
Rigid Base → Liquid Interactive Layer
```

例外是 Input：可用 Solid Input Body 承载文字，再用 Glass Focus / Action Layer 承载 Clear、Dropdown、Voice、Submit。

## 反模式

让所有内容持续流动或层层实时模糊、所有 Card 强阴影、用明显 3D 挤出制造厚度、写实陶瓷/塑料/金属纹理、Card inside Card inside Card、Solid Hover 变成液体。
