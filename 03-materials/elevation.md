# 03.4 — Elevation & Layer Model

Lumina 的空间不是平面 UI 加阴影，而是不同材质、表面形态和空间高度组成的数字环境。

## L0–L6

```text
L6  System / Modal Overlay
L5  Floating Flowing Glass
L4  Fitted Flowing Glass Controls
L3  Solid Topography
L2  Solid Content Surface
L1  Solid Base Surface
L0  Canvas
```

| 层级 | 名称 | 主要职责 |
|---:|---|---|
| L0 | Canvas | 背景、环境光、色温、材质对比基础 |
| L1 | Solid Base Surface | 主内容区、Sidebar 底板、主体 Sheet |
| L2 | Solid Content Surface | Task / Event / Project / Message / Setting 内容 |
| L3 | Solid Topography | Embedded / Raised / Recessed / Scored 局部地形 |
| L4 | Fitted Flowing Glass | 嵌合在 Recess 中的 Button、Toggle、Tab、Action |
| L5 | Floating Flowing Glass | Toolbar、Popover、Context Menu、Command Palette |
| L6 | Overlay | Modal、Critical Dialog、全屏遮罩、System Prompt |

## 规则

- Elevation 表达空间关系，不等于重要性；重要性优先用 Typography、Color、Position、Spacing。
- 一个界面区域默认只有一个主要光源，推荐 Top Left / Upper Ambient；Solid Edge、Raised、Recessed、Scored、Glass Highlight、Shadow 必须共享它。
- `shadow.contact / low / medium / high` 依次服务于接触、Card、Popover/Toolbar、Modal/Floating。越高越大越柔，不是越来越黑。
- L6 正常情况下最多一个主 Overlay，避免无限叠加。
- L4 的标准关系是 `Solid → Recess → Flowing Glass`；L5 的 Glass 更独立、折射略明显，但仍避免强烈悬浮。

> **Depth should explain relationships, not decorate surfaces.**

清透模式可以改变 L1–L3 的外观，不改变其内容职责。层级数字是设计关系，不是固定 z-index、像素厚度或每层独立实时滤镜；按平台实现和遮挡关系确定绘制。
