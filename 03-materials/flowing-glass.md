# 03.1 — Flowing Glass

**Flowing Glass — 流光玻璃**不是普通透明玻璃，也不是单纯 Blur。它是一种有厚度、光泽、流动性、表面张力、折射感和交互记忆的数字材质。

> **A living transparent surface.**  
> 一种活着的透明表面。

## 材质结构

```text
Surface Film   高光、水痕、涟漪、触摸反馈
Glass Body     厚度、Tint、Transparency
Refraction     Blur、Distortion、背景轻微位移
Environment    玻璃必须与背后的环境发生关系
```

它应表现为通透、湿润、有厚度、有光泽、柔软、流动、精致；边缘像水滴形成的表面张力，看得见但难以指出明确轮廓。避免白色描边、霓虹外发光、高饱和彩虹色散和游戏装备式反光。

## 光与厚度

厚度优先通过 Edge Highlight、内部折射、内阴影、边缘透明度变化和背景轻微位移建立。Blur 只是组成部分，不等于 Glass；`Thin / Standard / Dense Glass` 可使用低 / 中 / 高 Blur，但 Blur 越高不代表越高级。

高光应大范围、柔和、低透明度、缓慢变化。Glass Tint 存在于玻璃本体而非纯色覆盖，可有 `Clear / Blue / Cyan / Green / Amber / Rose / Violet / Smoke` 等变体，默认低到中饱和。

## 交互响应

### Pointer Trace — 水痕

指针划过时，局部折射、高光拖尾、透明度和亮度发生短暂变化。生命周期：

```text
Pointer Enter → Surface Disturbance → Short Trace → Viscosity Decay → Rest
```

不是画一条明显线。速度越快，拖尾可更长但透明度更低；默认衰减约 300–500ms。

### Click Ripple — 涟漪

不是纯色圆圈，而是一次液体表面冲击：

```text
Impact → Compression → Circular Wave → Refraction Change → Damping → Rest
```

主要改变 Surface Normal、Refraction、Highlight 和 Edge Lighting，初始建议 350–550ms。

### Etched Ink — 蚀刻墨文字

文字像先蚀刻进玻璃，再在刻痕中填入黑色墨水：`Ink + Engraving + Edge Reflection`。默认使用 Ink Black、Charcoal 或 Deep Graphite；用户第一眼应先读到文字，第二眼才发现材质细节。

## 状态与降级

状态至少包括 `Rest / Hover / Pressed / Selected / Focused / Disabled / Dragging`。Glass 可表现为 `Calm / Active / Dormant`：活跃度本身就是状态语言。

性能等级：

```text
Full     Real-time Refraction + Highlight + Trace + Ripple + Distortion
Standard Blur + Highlight + Simple Ripple + Tint
Reduced  Semi-transparent Surface + Static Highlight + Border + Shadow
```

Reduce Motion 关闭 Water Trace、Surface Flow、Large Ripple、Morph Distortion；Reduce Transparency 将其降级为 Opaque / Semi-Opaque Surface + Clear Border + Basic Highlight。无论降级与否，交互语义和文字可读性不能消失。

