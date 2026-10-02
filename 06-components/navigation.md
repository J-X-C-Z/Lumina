# 06.4 — Navigation

导航表示位置、视图切换或页面级操作。当前目的地必须通过选择外观和语义状态共同标示；禁用目的地不得响应选择。层级按信息架构决定，不因玻璃材质而改变。

## 导航模式

底部导航适用于少量同级主目的地；Rail、Drawer 或 Sidebar 适用于更宽布局或较多目的地；Tab 用于同一层级中的并列内容。Toolbar/Top Bar 承载当前页面标题、返回和少量相关动作。Command Bar 用于可搜索/可发现的命令集合，不等同于目的地导航。

Flutter 固定控件目录含 `LuminaNavigationBar`、`LuminaNavigationRail`、`LuminaNavigationDrawer`、`LuminaTabs`、`LuminaBottomAppBar` 与 `LuminaTopBar`。这些组件使用 Lumina 外观并按适用场景复用 Flutter SDK 的选择、焦点、滚动或 TabController 行为。共享选择状态由宿主维护；组件不负责业务路由。

## Segmented 与选择镜片

少量、互斥的视图选项可采用凹槽轨道与移动镜片。Flutter `LuminaSlidingSelection` 负责在标签上方绘制镜片并忽略命中测试；支持长按拖动的宿主选择控件可连续拖动，释放时提交最近选项。切换目标时弹簧保留当前位移和速度。减少动态效果、高对比或减少透明度设置下，仍须保留清晰静态选中态。

## 浮动顶栏与滚动

Flutter `LuminaFloatingHeader` 只固定顶部胶囊。构建器提供的 inset 应用于滚动内容的 padding，使列表内容可以从玻璃后方经过；日期导航等滚动内容放在滚动区域内。顶栏有模糊底色时，底层已模糊的控件应关闭重复 backdrop blur，避免叠加滤镜。

Top Bar 的点击区须满足宿主平台触控/键盘要求。Flutter紧凑顶栏采用上下各4逻辑像素内边距及至少48逻辑像素内容区；完整顶栏内容token为56；长按导航拖动时镜片压缩在凹槽边界内，每次接触触发一次原生 haptic。此处描述的是 Flutter 控件行为，不构成跨设备触感或性能验收结论。

桌面密度可影响布局尺寸，但不能以压缩为由移除可见焦点或键盘可达性。各平台的系统栏避让、窗口边缘和返回键行为由平台层说明。
