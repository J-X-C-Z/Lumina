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
motion.fast        140ms
motion.page        180ms
motion.standard    220ms
motion.fluid       420ms
```

这是 Lumina 当前共享 motion token 的基线；单个交互可按任务选择曲线，不能把 token 时长误当作每个动画的硬编码时长。Motion scale 可在 0–1 调整，系统禁用动画或 scale 为0时移除空间运动并保留状态转换；必要的短暂不带位移淡入可保留。物理滑动/弹簧应从当前值与速度重新定向，不能因目标变化而重置到起点。

缓动角色：`standard / enter / exit / solid / fluid`。Solid 强阻尼、少回弹；Fluid 允许轻微超调和黏性恢复，但不能弹来弹去。交互只使用适合该控件的操作方式；长按拖动不是所有控件的通用规则。

## 交互与过渡

- Hover：Solid 轻微 Elevation / Brightness；Glass 可改变高光或按平台能力响应指针。Pointer Trace、水痕与实时折射属于设计探索 / Web 实现方向，不是当前 Flutter 能力。
- Press：Solid 轻微向下压；Glass 使用已有的透明度、边缘和材质反馈。真实水波/折射波属于设计探索，不应作为 Flutter 现状描述。
- Morph：存在明确前后关系时优先 Shared Element / Shape Morph，例如 `Glass Button → Expanded Control → Panel`。
- Page Transition：同层导航使用轻位移、Fade、Shared Element；避免整个页面频繁左右飞入飞出。
- Loading：优先 Skeleton、Progressive Reveal、Material Activity；不要所有页面都转圈。

## 无障碍

Reduce Motion 遵循系统 `disableAnimations`，并支持 Lumina `motionScale=0`：移除位置位移和放大镜动态，折叠、选择等功能仍可操作并直接呈现目标状态。可保留必要的状态替换；不得依赖水痕、涟漪、形变或环境流动来表达操作结果。Reduce Transparency 或 High Contrast 时，玻璃使用不透明表面并关闭 backdrop blur，同时保持清晰边界与焦点可见性。

## 动效审查

每个动画都回答：它从哪里来？去哪里？改变了什么状态？用户是否能从中理解连续性？如果只是让页面“更酷”，删除或降级。

> **Nothing moves without meaning.**
