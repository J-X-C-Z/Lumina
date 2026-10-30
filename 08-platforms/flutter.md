# Flutter — 当前实现与验收

依据：Orialis 本地 `packages/lumina_ui` 截至 2026-10-31 的实现快照（包含本地未提交增量）；当前包约束 Flutter >=3.47.0 / Dart >=3.13.0，历史验证环境为 Flutter 3.47.4 / Dart 3.13.3，本轮未重测 SDK。公开 API 从 `package:lumina_ui/lumina_ui.dart` 导入；`lib/src/` 是实现细节。

## 主题与材质

`LuminaThemeData.liquidGlass` 默认为 false：默认雕刻材质；true：无颗粒清透材质。`LuminaTheme` 的 `highPerformanceMode` 默认为 true；常规模式须由宿主主动选择。材质选项与性能选项彼此独立。

`LuminaTheme.brightness` 接收宿主解析后的亮度。`LuminaThemeModeSelector` 使用 system/light/dark；偏好保存和系统亮度解析由宿主负责。`fontScale` 不替代系统 `MediaQuery.textScaler`；`spacingScale`、`radiusScale` 和 `motionScale` 控制对应表达，完整胶囊仍保持胶囊形状。

内置中文/英文提示由 `LuminaLocalizations.delegate` 提供，未注册时默认中文；业务内容由宿主翻译。系统字体是库的默认选择。示例单独附带 OFL 授权的中文字体，它不成为库或所有客户端的字体要求。

## 数值与绘制

共享颜色、间距、圆角、尺寸和时间来自 Orialis `packages/lumina_tokens/lumina.v1.json`；Flutter 消费生成 Dart const。规范的 [JSON](../10-tokens/lumina.v1.json) 是该版本的发布快照。

实际滤镜为 Flutter `ImageFilter.blur` Gaussian；sigma XS/S/M/L/XL 是 0/3.5/5.5/9/14。非高性能显式 backdrop chrome 通常使用 M；高性能 Surface 使用静态磨砂，显式 backdrop 选择井可使用 S；无障碍不透明分支不启用背景模糊。共享 JSON 的 glass 12/6 是抽象值，当前生成 `LuminaTokenGlass` 未接到 Flutter 滤镜策略，不能当作实际 sigma。Web CSS 参数也不是 sigma 的逐值等价。

背景模糊只在持久 chrome 或显式配置的选择井启用；重复行、菜单项和 Chip 使用绘制材质。已有模糊底座时关闭内部 `backdrop`，避免同一区域重复滤镜。正常模式根据刷新预算调节质量，不能以单张截图或局部测试承诺帧率。

## 行为与宿主边界

[28 类映射](../06-components/flutter-catalog.md) 区分 Lumina 绘制和 SDK 行为。现有公共构造器保留；`LuminaRadioGroup` 提供组内方向键遍历，`LuminaMenuItem` 提供玻璃菜单行。弹层继承触发处的 Lumina 主题、MediaQuery、方向与文字缩放。

`LuminaKeyboardScope` 把 Enter/Escape 接到宿主回调，编辑框保留自己的输入与提交行为。路由快捷键、数据库、任务传播、排序保存、账户隔离与同步属于宿主。折叠默认只保存在内存；宿主可注入 `LuminaCardStore`，多账户应更换实例。震动提供专用 handler 及通用 `effectHandler`，按选择、拖动、阈值和结果区分；详见[语义触觉](../04-motion/haptics.md)。

## 当前增量与验收边界

轻拟态、玻璃夹层、连续压力与缓存策略见[材质](../03-materials/neumorphic-glass.md)，页面/弹簧边界见[动效](../04-motion/motion-system.md)。高性能模式保留连续过渡；不能据旧版规范推断“平阴影 / 所有放大镜都移除”。

已读取 2026-10-31 本地完整组件回归日志（215 tests passed）及定向静态分析 No issues found；这是已有日志的核对，本次文档任务没有重新运行 Flutter 或生成安装包。基线 manifest 保存来源文件、日志与展示图的 SHA256。10 月 30 日的 HyperOS 原生记录覆盖导航选择触觉与去重，不覆盖 31 日新增全部动效。

规范的发布不同时发布 Orialis 工作树中的未提交实现；包声明与本地增量的发布边界列在[状态](../STATUS.md)。最新真机视觉、高刷新率性能、全部辅助技术与跨平台行为仍需专项验收。
