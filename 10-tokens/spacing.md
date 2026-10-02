# 10.3 — Spacing & Layout Tokens

```text
space.0  = 0     space.1  = 4     space.2  = 8
space.3  = 12    space.4  = 16    space.5  = 20
space.6  = 24    space.8  = 32    space.10 = 40
space.12 = 48    space.16 = 64    space.20 = 80
space.24 = 96

spacing.inline.xs / sm / md
spacing.stack.sm / md / lg
spacing.section
spacing.page

layout.page.padding.compact / standard / large
layout.content.compact / standard / wide / full
layout.gutter.sm / md / lg
layout.sidebar.width / compact
```

组件优先复用命名值。当前 spacing 中 item14、tight6 是已命名光学校正，control18 属于圆角 token；不能只按是否为4的倍数判定合规。完整映射见 [当前数值映射](implementation-mapping.md)。

