# 08.4 — Web

重点处理 Responsive、Browser Zoom、Keyboard、Pointer / Touch、Reduce Motion、Reduce Transparency 和性能。Flowing Glass 必须提供 Reduced 实现，不能因为模糊与折射让内容不可读或滚动性能下降。

Breakpoint 默认使用 `Compact <600 / Medium 600–1024 / Expanded 1024–1440 / Large >1440`，但优先根据内容开始放不下的位置调整。

## 当前实现边界

Orialis `packages/lumina_web` 为 React/TypeScript 基础组件实现；直接读取共享 JSON 并转换为CSS变量，使用原生HTML按钮、输入与dialog。支持system/light/dark偏好，系统模式追随浏览器；Web材质是Flutter绘制的CSS近似，不承诺像素一致或28类完整覆盖。

Canvas2D水波是Web增强；Three.js场景按需启用且不进入控件交互层。它们不使Flutter自动获得水痕、真实折射或同等性能。运行时成本与键盘/触控质量需单独检查；本轮没有新增Web运行验收结论。
