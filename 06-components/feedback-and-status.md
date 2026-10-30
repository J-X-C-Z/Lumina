# 06.5 — Feedback & Status

反馈说明发生了什么、当前进度和可采取的动作。状态色只是辅助；搭配文字、形状、图标或语义值，不用整页染色代替具体说明。

## Tooltip

Tooltip 为图标或不明显控件补充简短说明，不承载关键操作或唯一说明。Flutter `LuminaTooltip` 以 Lumina 玻璃绘制内容，并复用 SDK 的 hover/long-press 触发机制和语义 tooltip。触控端不能要求用户必须悬停才能理解控件；平台触发细节以 SDK 和平台层为准。

## Toast / SnackBar

用于短暂、非阻断的结果提示。消息简短，避免重要错误仅闪现后消失；有明确可逆动作时才提供操作。Flutter `showLuminaMessage` 显示 Lumina 消息 overlay，不要求宿主 `ScaffoldMessenger`。它继承触发上下文的主题/调色板并暴露 live-region 提示；消息文本和是否重试由调用方决定。

## Progress 与 Loading

可确定进度时显示数值/比例；未知时使用 indeterminate 状态。避免无意义的持续闪烁，减少动态效果时仍提供“正在加载”语义。Flutter `LuminaLinearProgress(value: null)` 为不确定进度，确定值范围是 0 到 1，并提供加载语义和值百分比；减少动态效果时停止循环动画。进度控件不管理异步任务或完成状态。

## Badge、Error、Success 与 Warning

Badge 只标记简短数量或状态，不应遮挡其锚定控件。Flutter `LuminaBadge` 可有文字 label；纯装饰点不含文字语义。错误、成功、警告应说明结果及下一步；颜色与图形样式需兼顾高对比和色觉差异。

## 触觉与结果

触觉按[语义规则](../04-motion/haptics.md)由宿主接入，不能以动画或振动已经发生推断数据保存成功。完成先等待业务回调，失败恢复条目并保留说明；减少动态效果仍表达结果。
