# Flutter 控件目录：固定 28 类

本页按 Flutter Material 3 组件目录固定映射 28 类 Lumina 控件，基线为 Flutter 3.47.4 / Dart 3.13.3。它记录 Lumina Flutter 包当前的覆盖面，不代表其他平台已有相同控件或行为，也不代替平台设备验收。新增 SDK 控件或升级基线时应重新核对目录。

“Lumina”表示 Lumina 负责该控件材质绘制和主要交互；“Lumina + SDK behavior”表示 Lumina 定义外观，而输入、焦点、手势、语义或 overlay 等行为部分复用 Flutter SDK。重复列表、chip 和菜单项不添加逐项实时 backdrop filter。

| 类别 | Flutter 控件目录项 | Lumina API | 外观/行为边界 |
| --- | --- | --- | --- |
| Actions | Common buttons | `LuminaButton`, `LuminaMaterialButton`（filled、tonal、elevated、outlined、text） | Lumina 绘制和交互 |
| Actions | FloatingActionButton | `LuminaFloatingActionButton` | Lumina |
| Actions | Extended FloatingActionButton | `LuminaFloatingActionButton(label: …)` | Lumina |
| Actions | IconButton | `LuminaIconButton` | Lumina |
| Actions | SegmentedButton | `LuminaSegmented<T>`, `LuminaMultiSegmented<T>` | Lumina 单选/多选外观，多选焦点复用 SDK |
| Communication | Badge | `LuminaBadge` | Lumina |
| Communication | LinearProgressIndicator | `LuminaLinearProgress` | Lumina |
| Communication | SnackBar | `showLuminaMessage` | Lumina overlay，不依赖 `ScaffoldMessenger` |
| Containment | AlertDialog | `showLuminaDialog`, `LuminaDialog` | Lumina |
| Containment | Bottom sheet | `showLuminaSheet` | Lumina |
| Containment | Card | `LuminaSurface` | Lumina |
| Containment | Divider | `LuminaDivider`, `LuminaEngravedDivider` | Lumina |
| Containment | ListTile | `LuminaListRow`, `LuminaListTile` | Lumina |
| Navigation | AppBar | `LuminaTopBar`, `LuminaPageScaffold` | Lumina |
| Navigation | Bottom app bar | `LuminaBottomAppBar`, `LuminaBottomActionBar` | Lumina |
| Navigation | NavigationBar | `LuminaNavigationBar` | Lumina |
| Navigation | NavigationDrawer | `LuminaNavigationDrawer` | Lumina |
| Navigation | NavigationRail | `LuminaNavigationRail` | Lumina |
| Navigation | TabBar | `LuminaTabs` | Lumina |
| Selection | Checkbox | `LuminaCheck` | Lumina |
| Selection | Chip | `LuminaChip` | Lumina 外观 + SDK 选择/删除行为 |
| Selection | DatePicker | `showLuminaDatePicker` | Lumina |
| Selection | Menu | `LuminaMenuAnchor`, `LuminaMenuItem` | Lumina 外观 + SDK 菜单/焦点行为 |
| Selection | Radio | `LuminaRadio<T>`, `LuminaRadioGroup<T>` | Lumina lens + SDK `RadioGroup`；Lumina 组启用兄弟遍历 |
| Selection | Slider | `LuminaValueSlider`, `LuminaContinuousSlider`, `LuminaRangeSlider` | 离散值由 Lumina 实现；连续/范围滑块用 Lumina 轨道和镜片、复用 SDK 行为 |
| Selection | Switch | `LuminaSwitch` | Lumina |
| Selection | TimePicker | `showLuminaTimePicker` | Lumina |
| Text input | TextField | `LuminaTextField` | Lumina 样式，保留 SDK 文本编辑机制 |

## API 差异与限制

`LuminaMenuItem` 是 Lumina 提供的菜单项 API，可避免调用方直接构造 Material 菜单项；`LuminaMenuAnchor` 仍接受 SDK 菜单子项和 builder。它们都用 Lumina 菜单材质，但 API 并非同一个构造方式。

`LuminaRadioGroup<T>` 包装 Flutter SDK 的 `RadioGroup<T>`，负责组值回调，并启用同组 Radio 的方向键遍历。单独使用 `LuminaRadio<T>` 时可按 SDK 上下文接入 `RadioGroup`；lens 只绘制选择，不承载焦点或点击。

日期选择器将首尾边界和初始日期归一到日历日，允许区间包含首尾两日；月份按钮受边界月份限制，方向键按天移动，Page Up/Page Down 按月移动。时间选择器提供小时/分钟步进，不等同于含日期/时区的完整日期时间控件。Lumina内置日期/操作文案支持中文与英文；宿主如使用其他SDK日期/文本组件，应配置相应Flutter localization。业务可选范围由调用方给出。

目录可在 Flutter 独立展示应用中逐项查看；行为、无障碍和设备验收边界见[Flutter 平台说明](../08-platforms/flutter.md)。覆盖所有 28 项的渲染不等于穷尽 Flutter 的全部行为，也不证明各设备上的视觉、屏幕阅读器或性能验收已经完成。
