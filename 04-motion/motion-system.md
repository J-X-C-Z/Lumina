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

## v0.3：连续按压与中断

手指落下即开始压力进度，按下、松开、拖动取消或重新按下都从当前显示状态接续。共用 `LuminaSurface` 的压力驱动表面深度、明暗阴影、边缘和轻量位移，不能只在两个 `pressed` 端点之间瞬间切材质。

物理按压/选择弹簧保留位置与速度；页面分支采用当前位移与透明度重新定向的缓动，两者无需共用同一种驱动器。不要把新目标重置为旧起点。内容与交互子树保持单份，变换节点持续存在；进入保存或禁用态不应重建编辑器、焦点或原有 state。

开关色与勾选、单选点、分段选中背景、导航文字/图标、滑块气泡和禁用透明度均应有中间过渡，同时保留即时语义状态。高性能模式保留轻量过渡，只降低绘制成本；减少动态效果才取消空间运动。

## 页面、滚动与保存

分支保留已挂载状态，仅活动分支参与布局与绘制；隐藏分支关闭 ticker、焦点、指针与语义。快速切换从当前透明度/位置接续，不复制两个可编辑页面叠着动画。

Orialis 手机版主应用与资讯共用滚动回弹策略，减少动态效果时使用非弹性滚动。这是宿主策略，不是所有平台必须开启回弹的 Core 规则。

完成操作先启动并等待业务保存成功，再给成功触觉与视觉闭合；保存不等待动画。失败保留条目并说明失败，页面离开不取消已启动的保存。动画只表现结果，不充当数据提交凭据。

[组件实际逐帧示例](../06-components/visual-reference.md) 展示静止、中间态和按下终态；[语义触觉](haptics.md) 规定何时反馈。
