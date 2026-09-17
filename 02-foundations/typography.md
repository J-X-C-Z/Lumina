# 02.2 — Typography

> **Typography should organize information before it decorates it.**  
> 字体首先组织信息，然后才塑造风格。

## 原则

层级明确、字重克制、阅读优先、平台自然、节奏安静。优先用 `Typography + Spacing` 建立结构，不用大量颜色、框线和卡片弥补排版不足。

## 角色与基线

| Role | 建议字号 | 字重 | 用途 |
|---|---:|---:|---|
| Display | 48–64 | Semibold | Hero / 品牌展示，少用 |
| Large Title | 32–40 | Semibold | 页面核心标题 |
| Title | 24–28 | Semibold | 页面、Dialog、模块标题 |
| Heading | 18–22 | Medium / Semibold | Section、Card Title |
| Body Large | 17–18 | Regular | 需要强调的正文 |
| Body | 15–16 | Regular | 默认正文 |
| Body Small | 13–14 | Regular | 辅助正文 |
| Label | 13–15 | Medium | Button、Tab、Navigation |
| Caption | 11–13 | Regular / Medium | 时间、元信息 |
| Numeric | 依场景 | Medium / Semibold | 时间、数据、指标 |
| Code | 依场景 | Mono | Code、ID、Logs |

推荐基础 Ramp：`56 / 36 / 28 / 20 / 18 / 16 / 14 / 14 / 12`。平台可微调，但层级关系应保持。

## 排版细节

- 字重优先 `Regular 400 / Medium 500 / Semibold 600 / Bold 700`；Bold 只做少量强强调。
- Display 行高约 `1.05–1.15`，Title `1.15–1.25`，Heading `1.25–1.35`，Body `1.45–1.65`。
- 中文默认不增加字距；英文标题可轻微收紧，Body 保持自然。
- 中英数混排需检查高度、基线和视觉重量；时间与表格优先 Tabular Figures。
- 长文本控制在约 `55–80 characters` 或 `600–760px`；默认左对齐。
- Markdown、Code、Blockquote、List、Link 都属于应用 UI，不能直接套浏览器默认样式。

## 字体架构

```text
font.ui       系统兼容的 UI 字体，默认
font.display  可选的品牌展示字体
font.mono     代码与技术数据
```

不强制所有平台使用同一字体文件；保持排版性格一致比字体名称完全相同更重要。支持 Dynamic Type、系统字体缩放和中文 fallback。

