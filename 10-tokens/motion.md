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
