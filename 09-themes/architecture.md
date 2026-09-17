# 09.1 — Theme Architecture

## Core 与 Theme

Core 定义不应频繁修改：spacing scale、语义颜色架构、材质角色、交互状态、无障碍和动效哲学。

Theme 可以覆写：

```text
brand.primary / secondary
glass.tint
solid.temperature
material.intensity
radius.personality
motion.expression
domain components
```

## Token 层级

```text
Primitive  neutral.* / blue.* / space.* / radius.* / duration.*
Semantic   color.text.* / color.surface.* / material.* / motion.* / shape.*
Component  button.* / input.* / navigation.*
Theme      theme.orialis.*
```

新增规则前询问：现有 Token 能否解决？这是通用还是项目需求？应改 Core 还是 Theme？是否破坏 Solid / Glass 语义？是否支持 Light / Dark、无障碍与跨平台降级？

