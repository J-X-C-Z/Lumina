# 语义触觉

触觉标记选择、阈值与结果，不为每次重绘振动。系统偏好和硬件能力优先；触觉不可用时，操作与视觉/语义反馈继续完成。

| `LuminaHaptics` 入口 | 语义 | 默认 Flutter 回退 |
| --- | --- | --- |
| `selection` / `tick` | 选择改变 / 离散刻度 | selectionClick |
| `longPress` / `dragStart` | 长按识别 / 开始拖动 | mediumImpact |
| `threshold(bool)` | 越过 / 退出有效阈值 | selectionClick |
| `toggle(bool)` | 开启 / 关闭 | selectionClick |
| `confirm` | 操作确认 | lightImpact |
| `reject` | 操作失败或拒绝 | heavyImpact |

调用顺序为专用 `selectionHandler` / `confirmHandler`（如适用），再到通用 `effectHandler`，否则使用 Flutter 回退。缺少插件时尝试回退；平台异常不阻断操作，系统抑制的反馈不替换成强制振动。库中的入口不代表每个宿主已接线所有效果，也不保证不同马达感受相同。

## 导航实例

Orialis 点击不同导航页，或长按拖动后提交不同页时触发一次 selection。重复点击当前页仍执行原回调，但不追加选择触觉；初始化、重建、禁用、取消拖动和拖回当前页不振。拖动拾起/边缘接触是独立语义，分别去重，不替代提交反馈。

Android 宿主通过系统触觉通道映射；已有 HyperOS 真机记录确认导航切换、同项去重和拖动提交。该记录没有覆盖所有效果、系统偏好组合或所有设备；主观强弱仍须实际体验。来源与验收层次见[状态](../STATUS.md)。
