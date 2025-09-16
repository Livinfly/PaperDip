# [Medusa: Simple LLM Inference Acceleration Framework with Multiple Decoding Heads](https://arxiv.org/abs/2205.14135)

## 动机

和 Spec decode 一样，LLM 自回归使得 decoding stage 的 memory-bound。

Spec decode 不够易用，不好找到合适的 draft model

## 贡献

提出 Medusa，不需要额外再找 draft model，只需要加入 decoding head，还可以有效缓解 distribution shift 的问题。

同时，给出两种场景的适用方法，适合不同计算资源、不同目的，同时应用经典的 temperature 接受策略，

让方法和原本的模型的策略更加融合。

对不同的训练数据集 / 训练方法提出适用的方法。

head 数量经验值 5 个足够。

## 方法

medusa-head，在最后一层附加几个 medusa-head；在 medusa 2 中，采用 common 的差异学习率（backbone 小，head 大），两阶段训练（先训 head，再一起调 / warmup）。

tree-attention，token 的 top1 准确度有  60pp，top5 却有 80pp，为了让主干模型更快地验证，采用 tree-mask，一次性验证多条

Typical acceptance，典型接受，启发于截断采样，不强求分布一致，根据temperature，适当扩大接受范围。

## 不足

探索非 transformer 架构 / 非语言任务的效果？

medusa-head 生成是独立的，不依赖上一个的输出，缺乏序列性，可能导致接受率低，但增加候选可能缓解这一现象。

（spec decode 同样）适合用于 batch size 小的时候

## 总结

。
