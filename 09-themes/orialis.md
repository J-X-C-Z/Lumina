# 09.2 — Orialis Theme

Orialis 是 Lumina Core 的第一个完整应用，不是另一套独立 Design System。

## 继承 Core

Orialis 继续使用 Lumina 的 Clarity、Restraint、Depth、Naturalness、Fluidity；Solid 承载消息、事件、任务和文件，Flowing Glass 承载 Send、Voice、确认、Agent 操作和导航。

## 主题覆写点

```text
theme.orialis.brand
theme.orialis.accent
theme.orialis.solid
theme.orialis.glass
theme.orialis.agent
theme.orialis.event
theme.orialis.task
```

初始气质可以更安静、轻盈、自然、通透，并让 Agent 的活跃、思考、调用工具、等待确认、执行成功和出错拥有专属状态表达；具体颜色和强度留到真实界面中验证。

## 不应覆写

不要因为 Orialis 是 Agent 产品就让所有区域持续发光，或推翻 Core 的可读性、间距、状态和平台原生行为。清透内容容器必须保持Calm与清晰地形，不增加逐行模糊或持续水波。

## 当前实例化

Flutter默认雕刻材质；桌面宿主可选择清透液态材质。命名色族mist/ocean/sage/amber/rose/lavender由同一主题机制派生。Orialis的优先级映射（rose重要且紧急、amber紧急、ocean重要、sage普通、mist未分类）属于Theme/领域规则，必须同时提供文字或图标。

任务与日程数据、子项传播、排序保存、路由、账户和同步保留在宿主，不进入Lumina Core。
