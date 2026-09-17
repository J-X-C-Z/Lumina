# 08.6 — Accessibility

材质效果永远不能破坏可访问性。至少支持 High Contrast、Reduce Motion、Reduce Transparency、Text Scaling、Keyboard Navigation、Screen Reader 和 Focus Visibility。

普通文字以约 4.5:1 对比度为基线，大字号和非文本交互对象按 WCAG AA 对应要求处理。状态不能只依靠颜色；焦点不能只靠微弱光泽；透明度降低后交互语义仍必须存在。

Hit Area 与视觉 Shape 分离：Mobile 约 44–48 起步，Watch 尽可能更大。动态字体放大时允许重排，不要用裁切隐藏重要信息。

