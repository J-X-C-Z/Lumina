# 10.5 — Motion Tokens

```text
motion.fast        140ms
motion.page        180ms
motion.standard    220ms
motion.fluid       420ms

motion.ease.standard
motion.ease.enter
motion.ease.exit
motion.ease.solid
motion.ease.fluid
```

组件动作语义：`motion.hover / press / focus / select / expand / collapse / page-enter / page-exit / ripple / trace / morph`。表达性动作必须支持 Reduce Motion 降级。

这些时间来自共享 JSON。未序列化的缓动/动作语义由平台实现，不是假定存在的字段。弹簧由位置与速度决定，不能硬性截成某个时长；减少动态效果保留操作与终点。

## 连续性约束

压力与选择弹簧继承当前位置/速度，页面缓动继承当前位移/透明度。高性能保留轻量动效，减少动态效果取消空间运动。共享时长未变，新增压力插值和触觉语义不是 JSON 字段。
