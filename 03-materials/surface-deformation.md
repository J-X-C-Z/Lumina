# 03.3 — Surface Deformation

**Solid 不是一张完全平坦的卡片，而是一块被塑形的信息表面。** 形变不是贴上去的装饰，而像同一块硬质材料经过精密加工形成的地形。

## 四种基础地形

| 结构 | 中文 | 空间动作 | 语义 |
|---|---|---|---|
| Embedded | 镶嵌 | 在表面中形成独立结构 | 属于 / 组织 |
| Raised | 凸起 | 表面向上生长 | 强调 / 锚点 |
| Recessed | 凹陷 | 表面向下形成 Well / Socket | 容纳 / 交互 |
| Scored | 划痕 | 沿表面留下浅刻线 | 保持整体下的区分 |

## Embedded — 镶嵌

子对象不是浮在主卡片上，而是嵌入主材料内部。适合相对独立、可单独选择、拥有独立状态的事件、项目、Filter 和 Status Item。颜色可以与主 Surface 有轻微差异，但仍保持 Rigid / Matte / Stable。

## Raised — 凸起

主表面本身向上生长。标题或核心数字周围可以形成类似火山口的缓坡与 Raised Rim：`Base → Slope → Raised Rim → Top Region`。用于 Section Title、页面锚点、核心数字和极重要信息；凸起本身不表示可点击。

## Recessed — 凹陷

Solid 表面局部形成凹槽或插槽。最重要的组合是：

```text
Solid Surface → Recessed Socket → Flowing Glass Control
```

它让 Confirm、Input Action、Toggle Cluster、Submit 等控件看起来像被硬质材料专门加工出的交互位置，而不是随便漂在卡片上。

## Scored — 精密划痕

Scored 不是 Divider、Border、独立 Card 或损坏纹理，而是一道干净、浅、精密的刻线。它让一张完整大卡片中的安排、设置行、属性和时间段产生小区别，同时保留“一体感”。

划痕结构是 `Edge Highlight → Shallow Groove → Inner Shadow → Surface`，颜色从材质与光照推导，不硬编码为灰色。支持 `subtle / standard / strong`，默认使用 subtle 或 standard；可为 Full、Inset、Partial，优先简单直线或简单曲线。

## 复杂度

```text
Level 0  Flat Solid
Level 1  + Embedded 或 Scored
Level 2  + Raised 或 Recessed
Level 3  Embedded + Raised + Recessed + Scored
```

Level 3 只用于代表性模块，例如 Today / Schedule。避免每个标题都隆起、每个按钮都挖槽、每条信息都有跑道卡片、不同地形使用不同光源，或为了 3D 牺牲阅读。

> **Separate without fragmenting.**  
> 区分，但不要割裂整体。

