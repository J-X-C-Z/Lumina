# 10.4 — Shape Tokens

```text
radius.none = 0
radius.xs = 4
radius.sm = 8
radius.md = 12
radius.lg = 16
radius.xl = 20
radius.2xl = 24
radius.3xl = 28
radius.full = Full

shape.control
shape.input
shape.card
shape.container
shape.floating
shape.overlay

border.width.hairline
border.width.standard
border.width.strong
```

语义 Shape 可由项目 Theme 覆写，但内外嵌套应继续遵守同心关系。

当前语义基线是 card24、control18、attachment14、capsule999。档位列表示可用尺度；组件采用已命名值及可测量的同心/肩部几何，见 [Shape](../02-foundations/shape.md)。
