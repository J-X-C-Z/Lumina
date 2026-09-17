# 04 — Motion System

> **Motion should reveal state, continuity and material.**  
> 动画应该说明状态、连续性和材质。

## 两种运动性格

```text
Solid Motion
Heavy · Stable · Controlled · Damped

Flowing Glass Motion
Light · Viscous · Fluid · Responsive · Continuous
```

Solid 像有质量的硬质物体；Glass 像有表面张力的液态玻璃。两者不能使用同一种反馈。

## 基线 Token

```text
motion.instant     80–100ms
motion.fast        120–160ms
motion.standard    180–240ms
motion.slow        280–360ms
motion.expressive  400–550ms
```

缓动角色：`standard / enter / exit / solid / fluid`。Solid 强阻尼、少回弹；Fluid 允许轻微超调和黏性恢复，但不能弹来弹去。

## 交互与过渡

- Hover：Solid 轻微 Elevation / Brightness；Glass 让 Highlight 跟随指针，加入轻微折射和短水痕。
- Press：Solid 轻微向下压；Glass 使用 `Compression → Ripple → Refraction Wave → Damping`。
- Morph：存在明确前后关系时优先 Shared Element / Shape Morph，例如 `Glass Button → Expanded Control → Panel`。
- Page Transition：同层导航使用轻位移、Fade、Shared Element；避免整个页面频繁左右飞入飞出。
- Loading：优先 Skeleton、Progressive Reveal、Material Activity；不要所有页面都转圈。

## 无障碍

Reduce Motion 关闭 Water Trace、Large Ripple、Morphing Distortion、Parallax、Environmental Flow；保留 Fade、Color、Basic Highlight 和状态替换。Reduce Transparency 时，Glass 改为不透明或半透明 Surface + 清晰边界。

## 动效审查

每个动画都回答：它从哪里来？去哪里？改变了什么状态？用户是否能从中理解连续性？如果只是让页面“更酷”，删除或降级。

> **Nothing moves without meaning.**

