# Status

## 当前版本

**Lumina · 光构 Design System v0.2**，修订日期 2026-10-02。规范版本不改变 Flutter 包 0.1.0 或共享 token 1.0.0 的版本。

## 已确定的语言

五个关键词：Clarity、Restraint、Depth、Naturalness、Fluidity。保留 Core / Theme 分层与 Embedded / Raised / Recessed / Scored 地形。内容保持稳定、操作可响应；深度解释关系，材质支持阅读。

## 已实现并用于本次修订

Flutter 固定 28 类目录已使用 Lumina 自有材质。菜单、单选、滑块等复用 SDK 的焦点、语义、手势或浮层机制。默认雕刻模式与可选清透液态模式均保留深浅配色及不透明降级。

全局主题、六套派生配色、共享数值、可打断选择与折叠、日期/时间、瞬态反馈、完整中英文示例已落地。Web 为基础组件阶段，使用 CSS 材质近似；水波是 Web 增强，不代表 Flutter 具有实时折射或相同效果。

## 本次检查证据

- Flutter 控件库 106 项测试通过，`flutter analyze lib test` 无问题。
- 独立示例 4 项测试通过，静态检查和 Web release 构建通过；其中检查了 320px 窄屏、1.6 倍文字及中英文交互。
- 宿主的页面、导航与键盘兼容性定向 23 项测试通过。
- 本地浏览器实际检查浅色英文与深色中文清透材质，中文字形正常。

以上是本地实现证据，源文件指纹见 [implementation-baseline.json](08-platforms/implementation-baseline.json)。本规范推送不等于组件源码发布；检查覆盖不等于全平台验收。

## 保留的设计目标与待验收项

屏幕阅读器人工体验、各平台真机视觉、持续帧耗时、全部 Material 行为边缘仍需专项验收。颜色对比度是验收要求，未完成全部背景与状态的量化审计。真实光学折射、Flutter 指针水痕和全平台水波属于探索目标。

28 类是固定目录，不代表自动覆盖后续 SDK 新控件。平台 breakpoint、衍生材质参数和项目配色允许根据实测调整；共享 token 修改需同步映射和规范快照。
