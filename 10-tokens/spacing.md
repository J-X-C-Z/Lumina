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

组件不得任意新建 18、21 等值；先检查 16 或 20 是否已经足够。

