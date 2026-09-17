# 02.3 — Spacing & Layout

> **Space should reveal relationships, not merely separate objects.**  
> 空间应该表达关系，而不仅仅是把元素隔开。

## 基础规则

采用 `4pt Grid`：`4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 / 80 / 96`。

```text
space.0 = 0    space.1 = 4    space.2 = 8    space.3 = 12
space.4 = 16   space.5 = 20   space.6 = 24   space.8 = 32
space.10 = 40  space.12 = 48  space.16 = 64  space.20 = 80
space.24 = 96
```

空间关系分为：`Micro 4–8`、`Component 12–20`、`Section 24–40`、`Page 48–96`。同组元素的距离应明显小于组与组之间的距离。

## 默认布局

| 场景 | 默认值 |
|---|---|
| Page Padding — Watch | 12–16 |
| Page Padding — Mobile | 16–24，默认 20 |
| Page Padding — Tablet | 24–32 |
| Page Padding — Desktop | 32–48 |
| Card Padding | 16–24；紧凑 12–16；大型 24–32 |
| Icon + Text | 8；紧凑 6；大型 10–12 |
| Content Group Gap | 16 |
| Section Gap | 32；大型 48 |
| Reading Width | 600–760px |
| Sidebar | 220–280；Compact 64–88 |

Desktop 内容定义 `compact 480–560 / standard 640–760 / wide 960–1200 / full`。复杂页面可采用 Desktop 12 列、Tablet 8 列、Mobile 4 列，但 Grid 是约束工具，不是强制模板。

## 响应逻辑

Mobile 默认单列；Desktop 使用 Sidebar + Content，必要时 List + Detail；Watch / Vela 使用垂直堆叠。不要把 Desktop 横向布局简单缩小到 Mobile，也不要把手机 UI 缩小后塞进 Watch。

Breakpoint 基线：`Compact <600 / Medium 600–1024 / Expanded 1024–1440 / Large >1440`，实际项目应根据内容开始放不下的位置调整。

遵循 Safe Area；文字和主要交互回到主网格，图片、地图、时间轴等可 Edge-to-Edge。Overlap 与 Floating 只用于表达层级、连续性或空间关系。

## Density

默认 `Comfortable`；高信息密度工具可使用 `Compact`。Compact 主要减少 Padding、Gap、Row Height，而不是把所有字号整体缩小。

