# 02.4 — Shape

> **Roundness is a relationship, not a decoration.**  
> 圆润应该表达对象之间的关系，而不是单纯把每个角变圆。

## Soft Geometry

Lumina 的基础形状是 `Rounded Rectangle / Capsule / Circle`。Rounded Rectangle 是主体；Capsule 与 Circle 只承担明确职责。

```text
radius.none = 0   radius.xs = 4   radius.sm = 8
radius.md = 12    radius.lg = 16  radius.xl = 20
radius.2xl = 24   radius.3xl = 28 radius.full = Full
```

当前共享材质基线：`radius.control=18`、`radius.card=24`、`radius.attachment=14`、`radius.capsule=999`。这些数值由 token 1.0.0 定义；Primitive 档位用于其他规模和布局，不覆盖现有语义值。

## 形状关系

- 对象越大，允许圆角越大，但增长速度慢于对象尺寸增长。
- 嵌套容器采用同心关系：`inner radius ≈ outer radius − inset`，允许 ±2–4 的 Optical Adjustment。
- 支持 Continuous Corners 的平台优先使用系统能力，其他平台可降级为普通圆角矩形。
- Capsule 适合 Chip、Tag、Filter、Segmented Selection、状态标签和小型快捷操作；不默认用于大型 Card、Dialog、长文本容器。
- Circle 适合 Icon-only Button、Avatar、Status Dot、Radio、Page Indicator、FAB；视觉图标 20×20 不代表 Hit Area 只能 20×20。

## 默认形状配方

```text
Generic Control    18
Content Card       24
Attachment         14
Capsule Control    Full（语义值999，由实际尺寸形成胶囊）
Chip / Filter      Full
Icon Action        Circle
Avatar             Circle
```

Shape 还包括 `border.none / hairline / standard / strong`。优先顺序是 `Spacing → Surface Difference → Subtle Border → Strong Border`；Strong Border 留给 Focus、Selection、特殊状态和无障碍。

避免所有组件统一超大圆角、忽视角色强制所有控件使用同一种 Shape、重复套卡片、使用没有命名用途的随机尺寸、粗边框制造“高级感”，或为了统一而无视平台原生控件。

