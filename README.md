# Lumina · 光构 Design System v0.1

**Lumina（光构）**是这套个人设计语言的新品牌名称。

个人设计系统的第一版可执行基线：让复杂的东西显得清晰，让数字界面拥有自然的秩序与质感。

> **Stable Information · Fluid Interaction**  
> 稳定的信息，流动的交互。

## 如何阅读

这是一套嵌套式规范。先读上层原则，再按需要进入下层文件：

```text
01 Philosophy
    ↓ 为什么这样设计
02 Foundations
    ↓ 颜色、排版、空间、形状
03 Materials
    ↓ Solid 与 Flowing Glass 如何形成空间
04–05 Motion / Iconography
    ↓ 材质如何动、符号如何表达
06 Components
    ↓ 可复用的交互部件
07 Patterns
    ↓ 完整页面如何组织
08 Platforms
    ↓ 同一种语言如何适配不同设备
09 Themes
    ↓ 项目品牌如何继承与覆写
10 Tokens
    ↓ 将规范落到设计与代码
```

## 目录

- [01 — Design Philosophy](01-philosophy/design-philosophy.md)
- [02 — Foundations](02-foundations/README.md)：[Color](02-foundations/color.md) · [Typography](02-foundations/typography.md) · [Spacing & Layout](02-foundations/spacing-layout.md) · [Shape](02-foundations/shape.md)
- [03 — Materials](03-materials/README.md)：[Flowing Glass](03-materials/flowing-glass.md) · [Solid](03-materials/solid.md) · [Surface Deformation](03-materials/surface-deformation.md) · [Elevation](03-materials/elevation.md) · [Composition](03-materials/material-composition.md)
- [04 — Motion](04-motion/motion-system.md)
- [05 — Iconography](05-iconography/iconography.md)
- [06 — Components](06-components/README.md)
- [07 — Patterns](07-patterns/README.md)
- [08 — Platforms](08-platforms/README.md)
- [09 — Themes](09-themes/README.md)
- [10 — Tokens](10-tokens/README.md)
- [CHANGELOG](CHANGELOG.md) · [STATUS](STATUS.md)

## v0.1 的状态边界

相对稳定的核心是：五个设计关键词、Solid × Flowing Glass 的材质分工、Solid Topography，以及“材质服务于信息和交互”的总体语言。

02–05 的颜色、字体、间距、形状、动效参数和组件尺寸，是参考成熟设计体系后整理出的可用基线；它们会在 Orialis 和其他真实项目中继续修订，不需要现在一次性锁死。

## 使用规则

1. 优先复用现有语义 Token，再新增值。
2. 先判断这是 Lumina Core 规则还是项目 Theme 规则。
3. Solid 默认承载内容，Flowing Glass 默认承载交互。
4. 用空间、排版和材质建立层级，最后才使用装饰。
5. 所有材质和动效都必须有可读性、性能和无障碍降级方案。
