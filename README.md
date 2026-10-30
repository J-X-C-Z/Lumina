# Lumina · 光构 Design System v0.3

**稳定的信息，流动的交互。** Lumina 用清晰的层级、安静的内容表面和可响应的玻璃控件组织界面。

v0.3 根据截至 2026-10-31 的 Flutter 实现与验收记录修订：补齐轻拟态磨砂、玻璃夹层、连续按压、可打断过渡和语义触觉。保留五个设计关键词、Solid Topography 与固定 28 类目录。设计规范 v0.3、Flutter 包声明 1.0.0（仍未发布 pub.dev）和共享 token 1.0.0 分别计版。

## 阅读入口

| 层 | 文档 | 解决的问题 |
| --- | --- | --- |
| 原则 | [01 Philosophy](01-philosophy/design-philosophy.md) | 为什么这样设计 |
| 基础 | [02 Foundations](02-foundations/README.md) | 颜色、排版、空间和形状 |
| 材质 | [03 Materials](03-materials/README.md) | 雕刻与清透模式、空间与成本 |
| 动效 | [04 Motion](04-motion/motion-system.md) | 连续反馈、可打断与减少动态效果 |
| 图标 | [05 Iconography](05-iconography/iconography.md) | 符号语义 |
| 组件 | [06 Components](06-components/README.md) · [Flutter 28 类映射](06-components/flutter-catalog.md) | 外观、状态和行为 |
| 页面 | [07 Patterns](07-patterns/README.md) | 内容组织 |
| 平台 | [08 Platforms](08-platforms/README.md) · [Flutter 实现与验收](08-platforms/flutter.md) | 共享语言与平台差异 |
| 主题 | [09 Themes](09-themes/README.md) | Core 与项目主题 |
| 数值 | [10 Tokens](10-tokens/README.md) · [机器可读快照](10-tokens/lumina.v1.json) | 当前基线和映射 |

## 使用规则

内容保持 Calm，交互提供明确状态；两者都以可读性为前提。库默认雕刻材质保留哑光承托与微地形；清透模式使用无颗粒表面、薄边缘和柔和阴影。宿主还可选择轻拟态同材质凹凸，以及磨砂井＋内容＋清透盖层的玻璃夹层。清透内容容器仍保持稳定层级，不持续流动。

优先使用现有语义 token。状态不能只靠颜色；焦点必须可见；减少动态效果、降低透明度与高对比度必须保留操作能力。平台共用数值与语义，不承诺同一绘制器、相同模糊参数或全部行为已经验收。

## 状态与来源

[STATUS](STATUS.md) 记录已实现、已检查和待验收的边界；[CHANGELOG](CHANGELOG.md) 记录修订原因；[实现基线](08-platforms/implementation-baseline.json) 保存源文件指纹与检查记录。

本仓库发布设计规范和数值快照。Flutter/Web 实现在 Orialis 的 `packages/lumina_ui` / `packages/lumina_web`；本次规范推送不发布这些未提交源码。v0.1 / v0.2 ZIP 保留为历史归档，当前可下载 [Lumina-Design-System-v0.3.zip](https://github.com/J-X-C-Z/Lumina/raw/refs/heads/main/Lumina-Design-System-v0.3.zip)。

[最新材质规则](03-materials/neumorphic-glass.md) · [连续按压动效示例](06-components/visual-reference.md) · [语义触觉](04-motion/haptics.md)
