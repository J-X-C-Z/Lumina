# 03.1 — Flowing Glass

**Flowing Glass — 流光玻璃**不是普通透明玻璃，也不是单纯 Blur。它是一种有厚度、光泽和环境关系的数字材质。Lumina 定义两种视觉模式：默认的**雕刻玻璃**（有细微纹理与蚀刻感）和可选的**清透液态玻璃**（无纹理、以柔和漫射高光与阴影表现通透感）。它们是材质绘制模式，不代表不同的模糊算法。

> **A living transparent surface.**  
> 一种活着的透明表面。

## 材质结构

```text
Surface Film   高光与交互反馈（按平台能力选择）
Glass Body     厚度、Tint、Transparency
Backdrop       裁剪后的 Gaussian blur（仅明确启用的表面）
Environment    玻璃与背后的环境建立关系
```

它应表现为通透、湿润、有厚度、有光泽、柔软、流动、精致；边缘像水滴形成的表面张力，看得见但难以指出明确轮廓。避免白色描边、霓虹外发光、高饱和彩虹色散和游戏装备式反光。

## 光与厚度

厚度优先通过边缘高光、内阴影、边缘透明度变化和层次建立。真实折射、背景位移和水痕属于设计探索或具备相应图形能力的平台实现，不应被当作 Flutter 当前能力。Blur 只是组成部分，不等于 Glass；Blur 越高不代表越高级。

高光应大范围、柔和、低透明度、缓慢变化。Glass Tint 存在于玻璃本体而非纯色覆盖，可有 `Clear / Blue / Cyan / Green / Amber / Rose / Violet / Smoke` 等变体，默认低到中饱和。

## 交互响应

### Pointer Trace — 水痕

**设计探索 / Web 实现方向。** 指针划过时，局部折射、高光拖尾、透明度和亮度可发生短暂变化。此效果不属于当前 Flutter 控件的已实现能力。生命周期：

```text
Pointer Enter → Surface Disturbance → Short Trace → Viscosity Decay → Rest
```

不是画一条明显线。速度越快，拖尾可更长但透明度更低；设计探索的衰减建议约 300–500ms。

### Click Ripple — 涟漪（设计探索）

不是纯色圆圈，而是一次液体表面冲击：

```text
Impact → Compression → Circular Wave → Refraction Change → Damping → Rest
```

主要改变表面法线、折射、高光和边缘照明；设计探索建议 350–550ms。当前 Flutter 实现不应据此宣称有真实水波或折射效果。

### Etched Ink — 蚀刻墨文字

文字像先蚀刻进玻璃，再在刻痕中填入黑色墨水：`Ink + Engraving + Edge Reflection`。Light采用深色Ink，Dark采用明亮Ink；蚀刻高光不能降低文字主体的对比度；用户第一眼应先读到文字，第二眼才发现材质细节。

## 状态与降级

状态至少包括 `Rest / Hover / Pressed / Selected / Focused / Disabled / Dragging`。Glass 可表现为 `Calm / Active / Dormant`：活跃度本身就是状态语言。

性能策略（Flutter）：

```text
Normal          裁剪后的 Gaussian BackdropFilter；sigma 5.5（BlurM）；宿主显式关闭高性能模式时使用
High-performance sigma 3.5（BlurS）；减少阴影成本并停用移动放大镜层
Reduced motion  不改变模糊预算；停用位置运动/放大镜等动态效果
Reduced transparency / High contrast  不透明材质，不应用 backdrop blur
```

Flutter 使用 `ImageFilter` Gaussian sigma：BlurXS 0、BlurS 3.5、BlurM 5.5、BlurL 9、BlurXL 14。常规模式玻璃导航使用BlurM，默认开启的高性能模式使用BlurS；帧预算自适应在连续慢帧后降低模糊、稳定后恢复，并保留 BlurS 下限。该实现没有自定义降采样或 Dual Kawase 后端。实时指针轨迹、水波和真实折射仍是设计探索或平台专属实现，不属于 Flutter 已实现能力。

Reduce Motion 遵循系统禁用动画设置，也支持 `motionScale=0`；它关闭位置运动与放大镜等动态效果，不改变控件语义。Reduce Transparency 或 High Contrast 使用不透明表面并关闭 backdrop blur。无论降级与否，交互语义和文字可读性不能消失。
