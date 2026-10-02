# 08.6 — Accessibility

材质效果永远不能破坏可访问性。至少支持 High Contrast、Reduce Motion、Reduce Transparency、Text Scaling、Keyboard Navigation、Screen Reader 和 Focus Visibility。

普通文字以约 4.5:1 对比度为基线，大字号和非文本交互对象按 WCAG AA 对应要求处理。状态不能只依靠颜色；焦点不能只靠微弱光泽；透明度降低后交互语义仍必须存在。

Hit Area 与视觉 Shape 分离：Mobile 约 44–48 起步，Watch 尽可能更大。动态字体放大时允许重排，不要用裁切隐藏重要信息。

## 当前控件执行要求

Flutter 交互目标基线为48逻辑像素；视觉镜片、单选圆点和图标可以更小。Tab遍历与Enter/Space激活适用于可操作按钮/开关；组内方向键、RTL、Home/End按各组件职责实现，编辑框保留原生输入行为。焦点轮廓不依赖轻微材质高光。

语义应包含名称、角色、选中/勾选/禁用状态和适用的值/动作。复合按钮避免重复可操作节点；Chip的选择与删除是两个动作；暂不可用的项不能仅降低透明度而继续响应。消息提供live-region提示。

系统禁用动画或motionScale=0走减少动态效果路径；高对比与reduceTransparency使用不透明材质、关闭背景模糊。弹层继承触发处设置，不能恢复为另一套字号或亮度。缩放允许换行和局部滚动，导航滚动应限定在组件自身视口。

对比度数值是验收目标，本轮没有覆盖所有材质组合的量化测试。自动语义检查、320px/1.6倍示例测试和部分2倍字号测试不替代真实辅助技术或全部设备验收。
