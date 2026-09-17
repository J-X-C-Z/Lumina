# 06.3 — Containers

## Card

默认是 Solid Material，可使用 Flat、Embedded、Raised、Recessed、Scored。不要默认把内容卡做成 Glass，也不要每一行都拆成独立 Card。

## List

优先 `One Solid Surface + Spacing + Scored`。同一组内容关系很强时使用 Scored；相对独立且有单独状态时使用 Embedded。

## Dialog

```text
Solid Dialog + Flowing Glass Actions
```

内容主体稳定，按钮负责交互。Dialog 通常位于 L6，但同一时间最多一个主 Overlay。

## Popover / Context Menu

临时交互 Surface 可使用 Floating Flowing Glass；如果包含复杂长内容，内部加入 Solid Content Region。

## Sheet / Panel

大型 Sheet 更接近 Solid Base / Content Surface；只有交互控件使用 Glass。顶部圆角基线约 20–28，底部是否圆角由平台决定。

