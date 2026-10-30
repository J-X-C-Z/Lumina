# 06.1 — Buttons

按钮表达可执行操作。用层级、文案和状态区分操作优先级；材质不得削弱文字、图标、焦点或禁用状态的辨识度。

## Primary、Secondary 与 Destructive

- **Primary**：每个局部操作区突出最重要的提交或继续操作。Lumina Flutter 的 `LuminaButton`、`LuminaMaterialButton` 提供 filled、tonal、elevated、outlined、text 等外观；外观不改变调用方提供的回调语义。
- **Secondary**：用于次要操作。若邻近控件已有强烈玻璃效果，改用稳定、低对比的实色层级。
- **Destructive**：使用明确动词和危险语义色；需要确认时由调用方提供确认流程。不能仅凭红色表达危险，也不在组件内推断业务后果。

## Icon Button 与 FAB

图标按钮应有可理解的语义标签；只有图形本身清晰且上下文充分时才省略可见标签。图形大小与命中区分开处理，触控端优先满足至少 48 logical pixels；更小的视觉图标仍须有足够大的交互区域。悬停和键盘焦点不可只靠颜色表示。

FAB 用于页面级高优先级动作；Extended FAB 仅在标签能帮助识别动作时使用。避免同屏多个同级 FAB。Flutter 目录对应 `LuminaFloatingActionButton`，提供图标或 `label` 形式。

## 状态与反馈

对适用的平台提供 Default、Hovered、Pressed、Focused、Disabled 状态。Loading 只在异步动作明确需要时展示，并避免重复提交；组件不推断请求成功或失败。按压反馈短促、局部，玻璃形变不能遮挡标签；减少动态效果时保留静态按压/焦点提示。

Material 外观由 Lumina 绘制不代表所有平台命中区或设备行为已验收；目标平台的触控、键盘和辅助技术行为须单独核对。

## 连续压力

共用表面的压力反馈从触点按下开始，松开、取消、重复按压均从当前状态接续；高性能模式保留动画。材质压力、阴影、侧壁与位移同步，不直接切换两个端点。禁用透明度平滑变化；禁用时立即停止事件响应并更新禁用语义，保留子树状态。减少动态效果使用静态终态。见[动效规则](../04-motion/motion-system.md)。
