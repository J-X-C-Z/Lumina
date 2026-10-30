# 06.2 — Inputs & Selection

输入和选择控件必须清晰显示当前值、可用操作与焦点。不要把颜色作为唯一状态信号；材质、标签、勾选符号和语义状态共同表达信息。

## TextField 与 Search

文本区域优先使用稳定、可读的实色或凹面容器；边框/底色变化之外还要保留标签、提示、错误说明和键盘焦点。清除、展开、语音等附属动作应有独立语义标签和命中区。Search 是带搜索语义的文本输入；搜索提交、建议列表和数据请求由宿主决定。

Flutter `LuminaTextField` 保留文本编辑、焦点和平台输入机制，并采用 Lumina 样式。不要据此推断所有 IME、屏幕阅读器或设备组合已完成验收。

## Switch、Checkbox 与 Radio

开关用于立即生效的二元设置；勾选框用于集合中独立的选择；Radio 用于互斥选项。呈现已选、未选、禁用以及可用的混合状态，状态变化应可通过形状/符号和语义识别。

Flutter `LuminaSwitch` 与 `LuminaCheck` 由 Lumina 控制视觉。`LuminaRadio<T>` 使用 Lumina lens 绘制选择状态，交互注册交给 SDK `RadioGroup`；包裹 `LuminaRadioGroup<T>` 可启用组内方向键遍历。它不代表所有桌面平台的焦点外观已通过人工验收。

## Slider、Segmented 与 Chip

- **Slider**：显示当前值；连续、离散与范围值各自说明适用场景。拖动和键盘调整均应保留可见焦点和值反馈。Flutter `LuminaValueSlider` 使用自有离散值实现；`LuminaContinuousSlider`、`LuminaRangeSlider` 使用 Lumina 轨道和 lens，并复用 Flutter SDK slider 行为。
- **Segmented**：用于少量、互斥的视图或选项。选择镜片跟随当前选择；键盘与焦点行为按宿主平台语义实现，不用纯动画代替可访问的选择状态。
- **Chip**：用于紧凑筛选、标记或带删除动作的项目。Chip 视觉由 Lumina 绘制，Flutter SDK 提供选择/删除等行为；单个 chip 的删除动作应与选择动作可区分。

Flutter的`LuminaSlidingSelection`提供导航、分段选择、开关与离散值滑块的井/镜片绘制；对应宿主控件支持长按镜片后连续拖动、释放时提交最近停止点；缩放镜片忽略命中测试，不截获标签。高对比或减少透明度时使用不放大的不透明外观；减少动态效果时仍能完成选择。

避免把所有输入、按钮、标签和导航都做成胶囊。减少动态效果、高对比和减少透明度设置应优先于装饰材质。

## 当前材质分支

轻拟态玻璃使用[磨砂井/内容/盖层](../03-materials/neumorphic-glass.md)随位置移动的夹层；非轻拟态分支继续提供井与镜片。放大镜并非高性能模式的一致开关，由材质、CardScope 和减少动态效果共同约束。开关勾选/颜色、单选点、分段与菜单选中背景、气泡值反馈连续变化；语义当前值保持正确，背景绘制不复制可交互内容。
