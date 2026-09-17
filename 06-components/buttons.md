# 06.1 — Buttons

## Button

### Primary

优先使用 Flowing Glass，用于页面主要操作；材质强度不应盖过按钮文字和页面内容。

### Secondary

根据上下文使用 Subtle Glass 或 Solid Control。若页面已有多个玻璃控件，优先用 Solid 降低竞争。

### Destructive

保留材质体系，通过 Error Tint + Clear Label 表达危险，不把按钮做成廉价红色大块。

## Icon Button

可用 Circle 或 Rounded Square。Circle 适合独立快捷操作、浮动控件和简洁 Toolbar；Rounded Square 适合 Dense Toolbar、并列功能和 Desktop Tool。若位于 Solid Card，优先作为 Flowing Glass Control。

## 间距与命中区

```text
Small   Horizontal 12 / Vertical 6–8
Medium  Horizontal 16 / Vertical 10
Large   Horizontal 20–24 / Vertical 12–14
```

Icon + Text 默认间距 8。视觉图形与 Hit Area 分开，Mobile 至少约 44–48，Watch 尽可能更大。

## 反馈

Solid Button 使用轻微压入和阻尼；Glass Button 使用局部 Compression、Ripple、Refraction 和恢复。不要对所有按钮使用长时间 Expressive Motion。

