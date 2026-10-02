# 10.1 — Token Architecture

```text
Layer 1 — Primitive
    原始色板、基础间距、圆角、时长
        ↓
Layer 2 — Semantic
    表达用途：text、surface、border、action、material、motion、shape
        ↓
Layer 3 — Component
    button、input、navigation 等组件状态
        ↓
Layer 4 — Theme
    theme.orialis.brand、glass、solid、domain
```

代码和设计稿默认使用 Semantic 或 Component Token，不直接硬编码 Hex、随机间距或阴影值。Primitive 只在建立和维护系统时使用。

## 概念与当前序列化

四层是语义组织目标。当前机器可读 JSON 按基础值分组，并未实现上文每个语义/组件名；实际映射见 [implementation-mapping.md](implementation-mapping.md)。新增字段必须有消费者、状态用途与平台降级策略，不能只为了让概念树更完整。
