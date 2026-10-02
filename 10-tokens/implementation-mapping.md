# 当前数值映射

本表描述 token 1.0.0 的真实用途。设计规范中的层级名可以更丰富；不存在的状态 token 不应被当成已实现 API。

| JSON 字段 | 设计用途 | 当前映射 |
| --- | --- | --- |
| color.*.ink / muted | 主文字 / 辅助文字 | Flutter 与 Web 基色 |
| color.*.paper / surface | Canvas / 内容表面 | 材质可派生 Raised/Recessed，不能把全部表面填成同一颜色 |
| color.*.accent / accentSoft | 操作、选择、焦点与轻强调 | 单一主 Accent；色板介入时派生整套颜色 |
| color.*.danger / outline | 危险提示 / 边界 | 错误仍需文字与语义 |
| spacing | page20 / pageTop12 / section24 / item14 / compact8 / tight6 / emptyState24 / controlGap8 | 当前紧凑布局；4pt 网格允许有命名的光学校正 |
| radius | card24 / control18 / attachment14 / capsule999 | 通用材质圆角；胶囊及圆形按内容/控件角色处理 |
| size | minimumControl48 / topBarContent56 / compactIcon17 / controlIcon24 | 逻辑单位；目标大小与图标、顶栏内容高度分别定义 |
| motionMs | fast140 / page180 / standard220 / fluid420 | 共享时间；弹簧选择不固定为420ms |
| glass | blur12 / highPerformanceBlur6 | 抽象材质值；当前 Flutter 实际 sigma 在平台策略定义，Web 使用 CSS 近似，不逐值互换 |

Light / Dark 的八个基础颜色由 [JSON](lumina.v1.json) 精确记录。Flutter 的六个命名配色 mist/ocean/sage/amber/rose/lavender 在 `LuminaCardPalette` 里派生：表面、凹槽、Accent 与文字一起计算。这些衍生 tint 不全在共享 JSON 中。

## 更新链

1. 在 Orialis `packages/lumina_tokens/lumina.v1.json` 修改需要变更的值。
2. 运行 `python3 packages/lumina_tokens/generate_flutter.py` 更新 Dart const；用 `--check` 验证没有漂移。
3. Web 直接导入 JSON；检查语义变量与材质映射，不假定 CSS 模糊等于 Flutter sigma。
4. 完成所影响的组件验收，再同步本仓库 JSON、规范表和实现基线。

本轮仅同步现值，没有改变组件的运行时数值。完整语义/组件 token 迁移或将生成链迁到本仓库需要单独决定。
