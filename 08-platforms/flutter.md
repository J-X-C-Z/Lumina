# Flutter — 当前实现与验收

依据：Orialis 本地 `packages/lumina_ui` 在 2026-10-02 的实现快照；Flutter 3.47.4 / Dart 3.13.3。公开 API 从 `package:lumina_ui/lumina_ui.dart` 导入；`lib/src/` 是实现细节。

## 主题与材质

`LuminaThemeData.liquidGlass` 默认为 false：默认雕刻材质；true：无颗粒清透材质。`LuminaTheme` 的 `highPerformanceMode` 默认为 true；常规模式须由宿主主动选择。材质选项与性能选项彼此独立。

`LuminaTheme.brightness` 接收宿主解析后的亮度。`LuminaThemeModeSelector` 使用 system/light/dark；偏好保存和系统亮度解析由宿主负责。`fontScale` 不替代系统 `MediaQuery.textScaler`；`spacingScale`、`radiusScale` 和 `motionScale` 控制对应表达，完整胶囊仍保持胶囊形状。

内置中文/英文提示由 `LuminaLocalizations.delegate` 提供，未注册时默认中文；业务内容由宿主翻译。系统字体是库的默认选择。示例单独附带 OFL 授权的中文字体，它不成为库或所有客户端的字体要求。

## 数值与绘制

共享颜色、间距、圆角、尺寸和时间来自 Orialis `packages/lumina_tokens/lumina.v1.json`；Flutter 消费生成 Dart const。规范的 [JSON](../10-tokens/lumina.v1.json) 是该版本的发布快照。

实际滤镜为 Flutter `ImageFilter.blur` Gaussian；sigma XS/S/M/L/XL 是 0/3.5/5.5/9/14。普通 chrome 使用 M，高性能使用 S；无障碍不透明分支不启用背景模糊。共享 JSON 的 glass 12/6 是抽象值，当前生成 `LuminaTokenGlass` 未接到 Flutter 滤镜策略，不能当作实际 sigma。Web CSS 参数也不是 sigma 的逐值等价。

背景模糊只在持久 chrome 或显式配置的选择井启用；重复行、菜单项和 Chip 使用绘制材质。已有模糊底座时关闭内部 `backdrop`，避免同一区域重复滤镜。正常模式根据刷新预算调节质量，不能以单张截图或局部测试承诺帧率。

## 行为与宿主边界

[28 类映射](../06-components/flutter-catalog.md) 区分 Lumina 绘制和 SDK 行为。现有公共构造器保留；`LuminaRadioGroup` 提供组内方向键遍历，`LuminaMenuItem` 提供玻璃菜单行。弹层继承触发处的 Lumina 主题、MediaQuery、方向与文字缩放。

`LuminaKeyboardScope` 把 Enter/Escape 接到宿主回调，编辑框保留自己的输入与提交行为。路由快捷键、数据库、任务传播、排序保存、账户隔离与同步属于宿主。折叠默认只保存在内存；宿主可注入 `LuminaCardStore`，多账户应更换实例。震动可通过 `LuminaHaptics.confirmHandler` 注入，不保证每个平台实际发出相同触感。

## 验收边界

当前库 106 项、示例 4 项、宿主定向 23 项测试通过；静态检查及示例 Web release 构建通过。浏览器观察到浅/深材质和正常中文显示。没有因此确认全部原生平台编译、真机输入、屏幕阅读器质量或持续性能。

代码仍在本地工作树；本次仅推送 Lumina 规范。源文件 SHA256 与检查日志指纹见 [实现基线](implementation-baseline.json)，它们标识已检查的内容，而不是某个公开源码 release。
