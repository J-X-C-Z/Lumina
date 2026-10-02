# 06.3 — Containers

容器负责表达内容分组、层级和可操作边界。材质的凸起/凹陷应对应真实层级，避免无意义的卡片套卡片与逐行加卡片。

## Card 与 List

默认使用稳定内容表面；Raised、Recessed、Embedded、Flat 等层级按承载关系选择。Flutter 对应 `LuminaSurface`。凹陷内容应能辨认其所属表面；共享表面可容纳相关列表项，使用间距或分隔线表达分组。

Flutter `LuminaCollapsibleCard` 默认展开，支持本地折叠状态存储适配器、保留已挂载内容并从顶部裁剪/显露。折叠后保留标题和简短状态；减少动态效果不改变展开/折叠结果。存储介质、账户隔离和业务持久化由宿主提供，控件不保存领域数据。

`LuminaExpandableCard` 是通用可展开容器。是否允许多个同时展开、展开内容和摘要由使用方决定；不能把特定产品的项目、里程碑或任务规则当作控件默认行为。

## Dialog、Popover、Menu 与 Sheet

Dialog 用于需要聚焦处理的短流程或确认，标题、内容和动作顺序清晰；通常一次只显示一个主模态层。Sheet 用于与当前上下文相关的较大或补充内容。Popover/菜单适合临时、短小的动作列表；内容较长时改用稳定内容区域或完整面板。

Flutter `showLuminaDialog`、`showLuminaSheet` 绘制 Lumina overlay；`LuminaMenuAnchor` 提供锚定菜单表面，`LuminaMenuItem` 提供 Lumina 菜单行 API。菜单定位、焦点遍历、关闭机制及手势依赖 Flutter SDK overlay/菜单机制。SDK 菜单项也能经主题获得 Lumina 样式；不要假定它们与 `LuminaMenuItem` API 相同。

弹层打开时保留触发上下文的 Lumina 主题、亮度和无障碍偏好；关闭、取消和选择后续动作由调用方处理。不同平台窗口边界、系统过渡和辅助技术行为可能不同。

## 日期与时间选择器

Flutter `showLuminaDatePicker` 将 `initialDate`、`firstDate`、`lastDate` 归一到日历日；初始日期必须位于含首尾日期的允许范围内，月份翻页和日期选择受边界约束。方向键按日移动，Page Up/Page Down 按月移动。`showLuminaTimePicker` 基于初始时间提供小时/分钟步进选择，不是完整日历日期时间控件，也不定义时区、预约规则或业务有效期。应用负责日期本地化配置和业务验证。

## 分隔线

分隔线用于说明分组或层级，不宜将每个列表行都框成独立卡片。Flutter 提供 `LuminaDivider` 与 `LuminaEngravedDivider`；凹刻效果必须保持足够的边界辨识度。
