# 10 — Tokens

Token 把设计语言落到代码。本轮共享 **token 1.0.0** 已用于 Flutter 与 Web；它和设计规范 v0.2、Flutter 包 0.1.0 独立版本化。

- [机器可读数值快照](lumina.v1.json) · [实际映射与同步](implementation-mapping.md)
- [Token Architecture](architecture.md)
- [Color Tokens](color.md)
- [Spacing & Layout Tokens](spacing.md)
- [Shape Tokens](shape.md)
- [Motion Tokens](motion.md)
- [Material Tokens](materials.md)

下层的语义命名是设计架构；JSON 当前使用 color/light/dark、spacing、radius、size、motionMs、glass 分组，并非完整的 DTCG token 包。不要声称所有概念语义名已进入代码。

Orialis `packages/lumina_tokens/lumina.v1.json` 是当前运行时生成链的来源。本仓库同名 JSON 是 2026-10-02 发布快照，保持字节一致；不要独立改成另一套运行时值。数值变更先更新运行时源、Flutter 生成文件及 Web 映射，再更新规范和快照。
