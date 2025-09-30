# [Attention Survey](https://attention-survey.github.io/files/Attention_Survey.pdf)

把 Attention 算子的优化划分为四类：

1. 硬件高效，如 FlashAttention
2. 压缩注意力，如 GQA
3. 稀疏注意力
4. 线性注意力，用其他的算子代替 softmax 算子

## 前置

简述了标准的 SDPA 注意力机制、GPU 的硬件特性、FlashAttention 的做法。

把注意力机制的使用场景分为非自回归的模型（如 Bert）、LLM 中的训练、LLM 的推理（Prefill + Decoding）

## 硬件高效

分为 prefill 和 decoding 两个阶段的注意力 kernel 的优化。

### Prefill

FlashAttention 已经变成至少 Prefill 阶段的基石算法，很难跳过块粒度的 QKV。

后面就是更低的精度，少的量化损失，新硬件带来的新的可 overlap 的量等等。

### Decoding

因为 q = 1，切分 seq 提高并行度（计算强度）；

改变 KV cache 的排布方式，提高 KV cache 的利用率；

观察不同运行阶段的激活值、参数的分布特征，提出合适的量化维度，降低量化误差；

不同场景下，动态最优的算子JIT；

动态调度等。

## 压缩注意力

暂略。

## 稀疏注意力
