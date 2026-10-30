# 03.5 — Material Composition

## 核心语法

```text
Solid carries content.
Flowing Glass carries interaction.
```

材质应让用户不用读说明，也能大致判断“这是内容，还是可以操作的东西”。

Lumina 有两种玻璃绘制模式：默认雕刻玻璃（细微纹理、蚀刻文字感）和可选清透液态玻璃（无纹理、柔和漫射高光与阴影）。清透液态玻璃也可作为 Calm 内容结构的容器，但内容的层级仍由 Solid Topography（Canvas、Solid、Raised、Recessed）表达；选用清透外观不等于把内容结构改成交互层。材质选择与交互行为分别决定。

## 推荐组合

| Pattern | 结构 | 适用 |
|---|---|---|
| A | Solid Card + Printed Content | 基础内容卡 |
| B | Solid + Scored Sections | 强相关信息组 |
| C | Solid + Embedded Items | 同一整体中的独立项目 |
| D | Solid + Raised Anchor | 标题、关键数字、结构锚点 |
| E | Solid + Recessed Socket + Flowing Glass | 标准 Lumina Signature Pattern |
| F | Solid Content + Floating Flowing Glass Toolbar | Desktop / Tablet 操作 |
| G | Solid Topography + Clear Glass Container | Calm 内容分组；玻璃只提供容器外观，Solid 层级仍组织内容 |

## 面积控制

普通内容页面可从以下比例开始：

```text
Solid / Neutral   75–90%
Flowing Glass      5–20%
Special Effect     <5%
```

这不是数学硬限制，目的是让玻璃保持珍贵，让内容仍是主角。

## 禁止组合

限制 `Glass inside Glass inside Glass`，也避免 Glass Content Card + Glass Button + Glass Navigation + Glass Background 的全玻璃页面。清透玻璃容器可用于内容结构，但应保留可辨认的 Solid Topography；连续嵌套会抹掉材质语义，并让透明、模糊和文字可读性互相干扰。真实折射不应作为 Flutter 当前实现的前提。

## 组合检查

1. 这是 Content 还是 Interaction？
2. 是否真的需要独立空间层级？
3. 是否能用 Spacing、Typography 或 Scored 完成分组？
4. 是否共享同一个光源和几何关系？
5. 是否有 Reduce Transparency、性能和可读性降级？

## 当前弹层例外

Flutter Dialog、日期/时间选择器、Sheet 和菜单容器使用不透明凸起承托，即使页面选择清透外观。Sheet 的 `LuminaCardScope` 还使内部交互行和按钮使用卡片材质，关闭选择井/镜片玻璃绘制与折射。弹层继续继承触发处主题、文字缩放和无障碍偏好；继承主题不等于所有子表面都透明。
